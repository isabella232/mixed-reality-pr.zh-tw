---
title: 安裝工具
description: MRTK-Unity，安裝工具檔頁面
author: polar-kev
ms.author: kesemple
ms.date: 03/02/2021
ms.localizationpriority: high
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、混合現實工具組、安裝、最新、工具、入門、基本、unity、visual studio、工具組、混合現實耳機、windows Mixed Reality 耳機、虛擬實境耳機、安裝、Windows、HoloLens、模擬器
ms.openlocfilehash: a22a032261f3734167b229618f40db112b43c0f7
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "102236959"
---
# <a name="install-the-tools"></a>安裝工具

取得為 Microsoft HoloLens 和 Windows Mixed Reality 沉浸式 (VR) 頭戴裝置建置應用程式所需的工具。 沒有個別的 SDK 可用於 Windows Mixed Reality 開發，您將使用 Visual Studio 搭配 Windows 10 SDK。

沒有混合實境裝置嗎？ 您可以安裝 [hololens 模擬器](https://docs.microsoft.com/windows/mixed-reality/develop/platform-capabilities-and-apis/using-the-hololens-emulator)  來測試混合現實應用程式的某些功能，而不需要 HoloLens。 您也可以使用 [Windows Mixed Reality](https://docs.microsoft.com/windows/mixed-reality/develop/platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator)  模擬器來測試您的混合現實應用程式是否有沉浸式耳機。

本頁面將引導您安裝搭配 Unity 使用 MRTK 所需的工具。 如果您有興趣探索其他混合現實開發平臺，請查看 [混合現實開發](https://docs.microsoft.com/windows/mixed-reality/develop/development?tabs=unity) 頁面的簡介。

您可以針對 Unity 的輸入模擬使用 [混合現實工具](https://github.com/Microsoft/MixedRealityToolkit-Unity)組，來測試各種類型的輸入互動，例如手動追蹤和眼睛追蹤。

|秘訣：將此頁面加入書簽並定期檢查，以保持最新版本的每個工具的最新版本，以供混合現實開發之用。|
|---|

## <a name="installation-checklist"></a>安裝檢查清單

| 工具 | 附註 |
|---------|---------|
| ![Windows 標誌](images/Windows10_logo.png)<br><br><a href="https://www.microsoft.com/software-download/windows10" target="_blank">**Windows 10** (手動安裝連結)</a><br><br>安裝最新版的 Windows 10，讓您電腦的作業系統符合您要建置混合實境應用程式的平台。  | **安裝 Windows 10** <br> 您可以透過 [設定] 中的 Windows Update 或藉由建立安裝媒體 (使用左欄中的連結)，安裝最新版的 Windows 10。 <br><br>請參閱[目前的版本資訊](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/mixed-reality-software)，以取得每個 Windows 10 版本可用的最新混合實境功能。 **在開發電腦上啟用開發人員模式** (在 [設定] > [更新與安全性] / [開發人員專用])。 <br><br> **企業和公司管理電腦的注意事項**<br>如果您的電腦由組織的 IT 部門管理，則可能需要與其連絡以便更新。 <br><br> **Windows 的 'N' 版本**<br> Windows 的 'N' 版本不支援 Windows Mixed Reality 沈浸式 (VR) 頭戴裝置。 |
| ![Visual Studio 標誌影像](images/visualstudio_logo.png)<br><br><a href="https://visualstudio.microsoft.com/downloads/" target="_blank">**Visual Studio 2019 (16.8 或更新版本)** (安裝連結)</a> <br><br>Windows 等的全功能整合式開發環境 (IDE)。 您將使用 Visual Studio 來撰寫程式碼、偵錯、測試及部署。 | **安裝 Visual Studio 2019** <br> 請確定您已安裝下列工作負載： <br><br>*● 使用 C++ 的傳統型開發*<br>*● 通用 Windows 平台 (UWP) 開發*<br><br>如果您要進行 HoloLens 的相關開發，請務必檢查 UWP 工作負載內是否有下列選用元件：<br><br>*● USB 裝置連線*<br><br>**Unity 的注意事項**<br>除非您刻意嘗試針對特定用途安裝更新 (非 LTS) 版本的 Unity，否則我們建議「不要」在 Visual Studio 安裝過程中安裝 Unity 工作負載，並改為安裝 **Unity 2019 LTS** 資料流，如下所述。<br><br>**已知問題**<br>Visual Studio 2019 16.0 版中的混合實境應用程式偵錯有一些已知問題。  請務必更新至 **Visual Studio 2019 16.8 版或更新版本**。 |
| ![Windows 標誌](images/Windows10_logo.png)<br><br><a href="https://developer.microsoft.com//windows/downloads/windows-10-sdk" target="_blank">**Windows 10 SDK (10.0.18362.0)** (手動安裝連結)</a> <br><br>提供用於在 HoloLens 2 上建置 Windows 10 應用程式的最新標頭、程式庫、中繼資料和工具。 | **若要建置 HoloLens 2 應用程式，您必須安裝 Windows SDK (組建 18362 或更新版本)。**<br> <br> 如果您只是要開發適用于桌上型 Windows Mixed Reality 耳機或 HoloLens (第1代) 的應用程式，您可以使用 Visual Studio 2019 所安裝的 Windows SDK。 |
| ![Visual Studio 標誌](images/HoloLensIcon.jpg)<br><br><a href="https://go.microsoft.com/fwlink/?linkid=2154784" target="_blank">**HoloLens 2 模擬器 (Windows 全像 20H2 2021 年2月更新)** (安裝連結： 10.0.19041.1134)</a><br> <br><a href="https://go.microsoft.com/fwlink/?linkid=2065980" target="_blank">**HoloLens (第 1 代) 模擬器** (安裝連結：10.0.17763.134)</a> <br><br>HoloLens 模擬器可讓您在沒有實體 HoloLens 的 HoloLens 虛擬機器映像上執行應用程式。<br> <br> | 如需開始使用模擬器的詳細資訊，請參閱[使用 HoloLens 模擬器](https://docs.microsoft.com/windows/mixed-reality/develop/platform-capabilities-and-apis/using-the-hololens-emulator)。<br> <br> **您的系統必須支援 Hyper-V**，模擬器安裝才能成功。 請參考下面的「系統需求」一節以取得詳細資料。 <br> <br> **HoloLens (第 1 代) 模擬器的注意事項** <br>. 如果您要使用 Visual Studio 2019 安裝 HoloLens (第 1 代) 模擬器，您必須取消選取 VS 範本，然後[從 Visual Studio Marketplace 加以安裝](https://marketplace.visualstudio.com/items?itemName=WindowsMixedRealityteam.WindowsMixedRealityAppTemplatesVSIX)。 |

## <a name="unity"></a>Unity

現在您已準備好 Windows 10、Visual Studio 和 Windows 10 SDK，讓我們使用 Unity 作為建立的引擎。

### <a name="1-download-the-latest-version"></a>1.下載最新版本

建議 [Unity LTS (長期支援)](https://unity3d.com/unity/qa/lts-releases) 資料流作為用來啟動新專案的最佳版本，並更新為其最新修訂版本，以挑選最新穩定的修正程式。

* 目前的建議是使用 [Unity 2019.4 LTS](https://unity3d.com/unity/qa/lts-releases?version=2019.4)。 也支援 Unity 2018.4 LTS。
* 如果您想要搭配 MRTK 使用 [Mixed Reality OpenXR](https://docs.microsoft.com/windows/mixed-reality/develop/unity/openxr-getting-started) 預覽功能，您將需要 Unity 2020.2 或更高版本。
* 如果您基於特定理由而需要使用不同的 Unity 版本，Unity 支援不同版本的並存安裝。

### <a name="2-install-the-mixed-reality-feature-tool"></a>2. 安裝 Mixed Reality 功能工具

「 [混合現實」功能工具](https://docs.microsoft.com/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool) 是一種新的方法，讓開發人員可以探索並將混合現實功能套件新增至 Unity 專案。

您可以依名稱或類別搜尋套件、查看其相依性，甚至在匯入之前查看專案資訊清單檔的建議變更。 驗證您想要的封裝之後，Mixed Reality 功能工具會將這些套件下載到您選擇的 Unity 專案。

#### <a name="importing-the-mixed-reality-toolkit"></a>匯入混合實境工具組

您可以遵循 [安裝和使用方式指示](https://docs.microsoft.com/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool#system-requirements) ，並選取混合現實工具組 Foundation 套件，以下載 Mixed reality 工具組套件。

如果您想要以手動方式從 Github 下載 MRTK 套件，請造訪 [Toolkit-Unity (Github) 的混合現實 ](https://github.com/microsoft/MixedRealityToolkit-Unity/releases)版本頁面。

### <a name="3-set-up-your-pc-for-mixed-reality-development"></a>3.設定您的電腦以便進行混合實境開發

Windows 10 SDK 最適合用於 Windows 10 作業系統。 Windows 8.1、Windows 8、Windows 7、Windows Server 2012、Windows Server 2008 R2 也支援此 SDK。 請注意，舊版作業系統不支援所有工具。

| 注意：您可以針對 HoloLens、VR 沉浸式耳機或兩者開發和部署應用程式。 視您的需求而定，請確定您符合下列需求。 |
|---|

#### <a name="for-hololens-development"></a>對於 HoloLens 開發

設定您的開發電腦以進行 HoloLens 開發時，請確定它符合 [Unity](https://docs.unity3d.com/Manual/system-requirements.html) 和 Visual Studio 的系統需求。 如果您想要在 HoloLens 裝置上執行您的應用程式，則必須遵循 [Windows 裝置入口網站安裝指示](https://docs.microsoft.com/windows/mixed-reality/develop/platform-capabilities-and-apis/using-the-windows-device-portal#setting-up-hololens-to-use-windows-device-portal)。 如果您打算使用 [HoloLens 模擬器](https://docs.microsoft.com/windows/mixed-reality/develop/platform-capabilities-and-apis/using-the-hololens-emulator)，您應確定您的電腦也符合 [HoloLens 模擬器系統需求](https://docs.microsoft.com/windows/mixed-reality/develop/platform-capabilities-and-apis/using-the-hololens-emulator#hololens-emulator-system-requirements)。

若要開始使用 HoloLens 模擬器，請參閱[使用 HoloLens 模擬器](https://docs.microsoft.com/windows/mixed-reality/develop/platform-capabilities-and-apis/using-the-hololens-emulator)。

如果您打算針對 HoloLens 與 Windows Mixed Reality 沈浸式 (VR) 頭戴裝置進行開發，請使用下一節中的系統建議和需求。

### <a name="hololens-troubleshooting"></a>HoloLens 疑難排解

設定開發人員模式呈現灰色

如果您在裝置上啟用開發人員模式時遇到問題，您可能不是[裝置擁有者](https://docs.microsoft.com/hololens/security-adminless-os)。 在多使用者模式中，第一個使用裝置的人員就是裝置擁有者，任何後續的使用者都不會擁有啟用 [開發人員模式] 或其他組態變更所需的權限。 不過，有一個例外狀況，那就是第一個使用者可能不是 Autopilot 環境中的裝置擁有者，這會在 [HoloLens 安全性文件](https://docs.microsoft.com/hololens/hololens2-compliance)詳述。

可能的解決方案包括：

* 在將裝置傳遞給其他使用者或開發人員之前，讓裝置擁有者開啟開發人員模式
* 建議您的 IT/MDM 系統管理員針對特定裝置或開發人員裝置群組啟用 [CSP 原則 ApplicationManagement/AllowDeveloperUnlock](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-allowdeveloperunlock) 。
此原則可經由[佈建套件](https://docs.microsoft.com/hololens/hololens-provisioning)或透過 [HoloLens 裝置的 MDM](https://docs.microsoft.com/hololens/hololens-mdm-configure) 來設定
* 使用 [Advanced Recovery Companion (ARC)](https://docs.microsoft.com/hololens/hololens-recovery)

| 注意：您可以在 HoloLens 裝置管理總覽中深入瞭解裝置管理。|
|---|

我無法透過 USB 部署

如果您無法直接透過 USB 部署應用程式，請確定您符合上述所有的安裝需求，並遵循我們的[逐步教學課程](https://docs.microsoft.com/windows/mixed-reality/develop/unity/tutorials/mr-learning-base-02#building-your-application-to-your-hololens-2)。

沈浸式 (VR) 頭戴式裝置需求

| 注意：下列指導方針是您的沉浸式 (VR) 耳機開發電腦目前的最小和建議的規格，並會定期更新。|
|---|

| 警告：請勿將此與 [最小的電腦硬體相容性指導方針](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)混淆，其概述您應以沉浸式 (VR) 耳機應用程式或遊戲為目標的取用者電腦規格。|
|---|

如果您的沉浸式耳機開發電腦沒有完整大小的 HDMI 和/或 USB 3.0 埠，您將需要 [介面卡 ](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs)來連接耳機。

目前某些硬體設定有[已知問題](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality)，尤其是具有混合式圖形的筆記型電腦。

. | 最小值 | 建議
--- |--- |---
處理器 | 筆記型電腦：Intel Mobile Core i5 第 7 代 CPU、採用超執行緒技術的雙核心 傳統型：Intel Desktop i5 第 6 代 CPU、採用超執行緒技術的雙核心或 AMD FX4350 4.2Ghz 四核心對等項目| Desktop： Intel Desktop i7 6 世代 (6 核心) 或 AMD Ryzen 5 1600 (6 Core、12個執行緒) GPU | 筆記型電腦：NVIDIA GTX 965M、AMD RX 460M (2GB) 對等項目或更高的 DX12 支援 GPU 傳統型：NVIDIA GTX 960/1050、AMD Radeon RX 460 (2GB) 對等項目或更高的 DX12 支援 GPU | 傳統型：NVIDIA GTX 980/1060、AMD Radeon RX 480 (2GB) 對等項目或更高的 DX12 支援 GPU
GPU 驅動程式 WDDM 版本 | WDDM 2.2 驅動程式
散熱設計功率 | 15W 或更大
圖形顯示連接埠 | 1個可用圖形顯示耳機的埠 (HDMI 1.4 或 DisplayPort 1.2 適用于60Hz 耳機、HDMI 2.0 或 DisplayPort 1.2 for 90Hz 耳機) 
顯示器解析度 | 解決方法：SVGA (800 x 600) 或更大的位元深度：每像素 32 位元的色彩
Memory | 8 GB 的 RAM 或更高 | 16 GB RAM 或更大
存放裝置 | >10 GB 的額外可用空間
USB 連接埠 | 適用於頭戴式裝置的 1x 可用 USB 連接埠 (USB 3.0 Type-A) 注意：USB 必須提供至少 900mA
Bluetooth | Bluetooth 4.0 (適用於周邊連線)

## <a name="next-development-checkpoint"></a>下一個開發檢查點

既然您已安裝工具，建議您遵循我們的 MRTK HoloLens 2 教學課程系列。
> [!div class="nextstepaction"]
> [HoloLens 2 教學課程系列](https://docs.microsoft.com/windows/mixed-reality/develop/unity/tutorials/mr-learning-base-02)