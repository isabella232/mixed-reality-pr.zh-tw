---
title: 安裝工具
description: 從這裡開始使用針對 HoloLens 和 VR 開發建議的最新版 Unity、Visual Studio 和工具。
author: thetuvix
ms.author: alexturn
ms.date: 05/11/2021
ms.topic: article
ms.localizationpriority: high
keywords: 最新狀態, 開始使用, 基本概念, unity, visual studio, 工具組, 混合實境頭戴式裝置, windows 混合實境頭戴式裝置, 虛擬實境頭戴式裝置, 安裝, Windows, HoloLens, 模擬器, unreal, openxr
ms.openlocfilehash: 1317d37fede9c714cebdbe7eb9b0c334f1e5fd1a
ms.sourcegitcommit: 6ade7e8ebab7003fc24f9e0b5fa81d091369622c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/19/2021
ms.locfileid: "112394352"
---
# <a name="install-the-tools"></a>安裝工具

取得為 Microsoft HoloLens 和 Windows Mixed Reality 沉浸式 (VR) 頭戴裝置建置應用程式所需的工具。 沒有個別的 SDK 可用於 Windows Mixed Reality 開發，您將使用 Visual Studio 搭配 Windows 10 SDK。

沒有混合實境裝置嗎？ 您可以安裝 [HoloLens 模擬器](platform-capabilities-and-apis/using-the-hololens-emulator.md)，以在沒有 HoloLens 的情況下測試混合實境應用程式的一些功能。 您也可以使用 [Windows Mixed Reality 模擬器](platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md)，針對沉浸式頭戴裝置測試您的混合實境應用程式。

建議您將 Unity 或 Unreal 遊戲引擎安裝為開始建立混合現實應用程式的最簡單方式。 不過，如果您想要使用自訂引擎，也可以針對 DirectX 進行建置。

如果您使用 Unity，則可以使用 [適用于 unity 的輸入模擬的混合現實工具](https://github.com/Microsoft/MixedRealityToolkit-Unity)組來測試各種類型的輸入互動，例如手動追蹤和眼睛追蹤輸入。 若為 Unreal 專案，請使用 [UX 工具外掛程式](https://github.com/microsoft/MixedReality-UXTools-Unreal) 來測試常見的輸入互動和使用者體驗功能。

>[!TIP]
>將這個頁面加入書籤並定期檢查，以在建議用於混合實境開發的每個工具最新版本上保持最新狀態。

<br>

## <a name="installation-checklist"></a>安裝檢查清單

| 工具 | 附註 |
|---------|---------|
| ![Windows 標誌](images/Windows10_logo.png)<br><br><a href="https://www.microsoft.com/software-download/windows10" target="_blank">**Windows 10** (手動安裝連結)</a><br><br>安裝最新版的 Windows 10，讓您電腦的作業系統符合您要建置混合實境應用程式的平台。  | **安裝 Windows 10** <br> 您可以透過 [設定] 中的 Windows Update 或藉由建立安裝媒體 (使用左欄中的連結)，安裝最新版的 Windows 10。 <br><br>請參閱[目前的版本資訊](/windows/mixed-reality/enthusiast-guide/release-notes-october-2018.md)，以取得每個 Windows 10 版本可用的最新混合實境功能。 **在開發電腦上啟用開發人員模式** (在 [設定] > [更新與安全性] / [開發人員專用])。 <br><br> **企業和公司管理電腦的注意事項**<br>如果您的電腦由組織的 IT 部門管理，則可能需要與其連絡以便更新。 <br><br> **Windows 的 'N' 版本**<br> Windows 的 'N' 版本不支援 Windows Mixed Reality 沈浸式 (VR) 頭戴裝置。 |
| ![Visual Studio 標誌影像](images/visualstudio_logo.png)<br><br><a href="https://visualstudio.microsoft.com/downloads/" target="_blank">**Visual Studio 2019 (16.8 或更新版本)** (安裝連結)</a> <br><br>Windows 等的全功能整合式開發環境 (IDE)。 您將使用 Visual Studio 來撰寫程式碼、偵錯、測試及部署。 | **安裝 Visual Studio 2019** <br> 請確定您已安裝下列工作負載： <br><br>*● 使用 C++ 的傳統型開發*<br>*● 通用 Windows 平台 (UWP) 開發*<br>*●使用 Unity 進行遊戲開發 (**如果打算使用 unity**)*<br><br>在 UWP 工作負載中， **確定已包含下列元件以供安裝**：<br><br>*● Windows 10 SDK 版本10.0.19041.0 或10.0.18362。0*<br>*●透過 USB) 將 USB 裝置連線 (部署/debug 至 HoloLens 的必要功能*<br>*● C + + (適用于 v142) 使用 Unity 時 (所需的通用 Windows 平臺工具)*<br><br>**關於 HoloLens (第1代) 和桌面 Windows Mixed Reality 耳機**<br>如果您只是要開發適用于桌上型 Windows Mixed Reality 耳機或 HoloLens (第1代) 的應用程式，您可以使用 Visual Studio 2017，並使用其所安裝的 Windows SDK。<br><br>**已知問題**<br>Visual Studio 2019 16.0 版中的混合實境應用程式偵錯有一些已知問題。  請務必更新至 **Visual Studio 2019 16.8 版或更新版本**。 |
| ![Visual Studio 標誌](images/HoloLensIcon.jpg)<br><br><a href="https://go.microsoft.com/fwlink/?linkid=2165258" target="_blank">**HoloLens 2 模擬器 (Windows 全像21H1 版，2021年6月更新)** (安裝連結： 10.0.20348.1007)</a><br> <br><a href="https://go.microsoft.com/fwlink/?linkid=2065980" target="_blank">**HoloLens (第 1 代) 模擬器** (安裝連結：10.0.17763.134)</a> <br><br>選用模擬器可讓您在 HoloLens 虛擬機器映射上執行應用程式，而不需要實體 HoloLens。<br> <br> | 如需開始使用選用模擬器的詳細資訊，請參閱 [使用 HoloLens 模擬器](../develop/platform-capabilities-and-apis/using-the-hololens-emulator.md) 。<br> <br> **您的系統必須支援 Hyper-V**，模擬器安裝才能成功。 請參考下面的「系統需求」一節以取得詳細資料。 <br> <br> **HoloLens (第 1 代) 模擬器的注意事項** <br>  必須使用 Visual Studio 2017，才能順利完成安裝。 如果您要使用 Visual Studio 2019 安裝 HoloLens (第 1 代) 模擬器，您必須取消選取 VS 範本，然後[從 Visual Studio Marketplace 加以安裝](https://marketplace.visualstudio.com/items?itemName=WindowsMixedRealityteam.WindowsMixedRealityAppTemplatesVSIX)。 |

## <a name="install-your-engine-of-choice"></a>安裝您選擇的引擎

現在您已準備好 Windows 10、Visual Studio 和 Windows 10 SDK，讓我們安裝並設定您所選擇的引擎。

> [!div class="nextstepaction"]
> [選擇您的引擎](choosing-an-engine.md)

## <a name="troubleshooting"></a>疑難排解

### <a name="setting-developer-mode-is-grayed-out"></a>設定開發人員模式呈現灰色

如果您在裝置上啟用開發人員模式時遇到問題，您可能不是[裝置擁有者](/hololens/security-adminless-os)。 在多使用者模式中，第一個使用裝置的人員就是裝置擁有者，任何後續的使用者都不會擁有啟用 [開發人員模式] 或其他組態變更所需的權限。 不過，有一個例外狀況，那就是第一個使用者可能不是 Autopilot 環境中的裝置擁有者，這會在 [HoloLens 安全性文件](/hololens/security-adminless-os#device-owner)詳述。

可能的解決方案包括：

* 在將裝置傳遞給其他使用者或開發人員之前，讓裝置擁有者開啟開發人員模式
* 建議您的 IT/MDM 管理員針對特定裝置或開發人員裝置群組啟用 CSP [Policy ApplicationManagement/AllowDeveloperUnlock](/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-allowdeveloperunlock)。
    * 此原則可經由[佈建套件](/hololens/hololens-provisioning)或透過 [HoloLens 裝置的 MDM](/hololens/hololens-mdm-configure) 來設定
* 使用 [Advanced Recovery Companion (ARC)](/hololens/hololens-recovery)

> [!NOTE]
> 您可以在 **[HoloLens 裝置管理](/hololens/hololens-csp-policy-overview)** 概觀中深入了解裝置管理。

#### <a name="i-cant-deploy-over-usb"></a>我無法透過 USB 部署

如果您無法直接透過 USB 部署應用程式，請確定您符合上述所有的安裝需求，並遵循我們的[逐步教學課程](unity/tutorials/mr-learning-base-02.md#building-your-application-to-your-hololens-2)。
