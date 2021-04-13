---
title: 安裝工具
description: 從這裡開始使用針對 HoloLens 和 VR 開發建議的最新版 Unity、Visual Studio 和工具。
author: thetuvix
ms.author: alexturn
ms.date: 04/13/2021
ms.topic: article
ms.localizationpriority: high
keywords: 最新狀態, 開始使用, 基本概念, unity, visual studio, 工具組, 混合實境頭戴式裝置, windows 混合實境頭戴式裝置, 虛擬實境頭戴式裝置, 安裝, Windows, HoloLens, 模擬器, unreal, openxr
ms.openlocfilehash: 40bf9930124e6f64197aaa5daca8b332dc741546
ms.sourcegitcommit: be79d8e9ebac553aabec7c57c44eee56123aa00e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/13/2021
ms.locfileid: "107369871"
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
| ![Windows 標誌](images/Windows10_logo.png)<br><br><a href="https://www.microsoft.com/software-download/windows10" target="_blank">**Windows 10** (手動安裝連結)</a><br><br>安裝最新版的 Windows 10，讓您電腦的作業系統符合您要建置混合實境應用程式的平台。  | **安裝 Windows 10** <br> 您可以透過 [設定] 中的 Windows Update 或藉由建立安裝媒體 (使用左欄中的連結)，安裝最新版的 Windows 10。 <br><br>請參閱[目前的版本資訊](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/release-notes-october-2018.md)，以取得每個 Windows 10 版本可用的最新混合實境功能。 **在開發電腦上啟用開發人員模式** (在 [設定] > [更新與安全性] / [開發人員專用])。 <br><br> **企業和公司管理電腦的注意事項**<br>如果您的電腦由組織的 IT 部門管理，則可能需要與其連絡以便更新。 <br><br> **Windows 的 'N' 版本**<br> Windows 的 'N' 版本不支援 Windows Mixed Reality 沈浸式 (VR) 頭戴裝置。 |
| ![Visual Studio 標誌影像](images/visualstudio_logo.png)<br><br><a href="https://visualstudio.microsoft.com/downloads/" target="_blank">**Visual Studio 2019 (16.8 或更新版本)** (安裝連結)</a> <br><br>Windows 等的全功能整合式開發環境 (IDE)。 您將使用 Visual Studio 來撰寫程式碼、偵錯、測試及部署。 | **安裝 Visual Studio 2019** <br> 請確定您已安裝下列工作負載： <br><br>*● 使用 C++ 的傳統型開發*<br>*● 通用 Windows 平台 (UWP) 開發*<br><br>如果您要進行 HoloLens 的相關開發，請務必檢查 UWP 工作負載內是否有下列選用元件：<br><br>*● USB 裝置連線*<br><br>**USB 連線能力注意事項**<br>您必須在安裝期間（預設不會核取）上，透過 USB 檢查 box **IP** 。 這是與 HoloLens over USB 通訊的必要項。<br><br>**Unity 的注意事項**<br>除非您刻意嘗試安裝較新的 (非 LTS) 版本的 Unity，否則建議您 *不要* 將 unity 工作負載安裝為 Visual Studio 安裝的一部分，而改為安裝 **unity 2019 LTS** 串流。<br><br>**已知問題**<br>Visual Studio 2019 16.0 版中的混合實境應用程式偵錯有一些已知問題。  請務必更新至 **Visual Studio 2019 16.8 版或更新版本**。 |
| ![Windows 標誌](images/Windows10_logo.png)<br><br><a href="https://developer.microsoft.com//windows/downloads/windows-10-sdk" target="_blank">**Windows 10 SDK (10.0.18362.0)** (手動安裝連結)</a> <br><br>提供用於在 HoloLens 2 上建置 Windows 10 應用程式的最新標頭、程式庫、中繼資料和工具。 | **若要建置 HoloLens 2 應用程式，您必須安裝 Windows SDK (組建 18362 或更新版本)。**<br> <br> 如果只要針對傳統型 Windows Mixed Reality 頭戴式裝置或 HoloLens (第 1 代) 開發應用程式，您可以使用 Visual Studio 2017 所安裝的 Windows SDK。 |
| ![Visual Studio 標誌](images/HoloLensIcon.jpg)<br><br><a href="https://go.microsoft.com/fwlink/?linkid=2160829" target="_blank">**HoloLens 2 模擬器 (Windows 全像20H2 版，2021年4月更新)** (安裝連結： 10.0.19041.1144)</a><br> <br><a href="https://go.microsoft.com/fwlink/?linkid=2065980" target="_blank">**HoloLens (第 1 代) 模擬器** (安裝連結：10.0.17763.134)</a> <br><br>HoloLens 模擬器可讓您在沒有實體 HoloLens 的 HoloLens 虛擬機器映像上執行應用程式。<br> <br> | 如需開始使用模擬器的詳細資訊，請參閱[使用 HoloLens 模擬器](../develop/platform-capabilities-and-apis/using-the-hololens-emulator.md)。<br> <br> **您的系統必須支援 Hyper-V**，模擬器安裝才能成功。 請參考下面的「系統需求」一節以取得詳細資料。 <br> <br> **HoloLens (第 1 代) 模擬器的注意事項** <br>  必須使用 Visual Studio 2017，才能順利完成安裝。 如果您要使用 Visual Studio 2019 安裝 HoloLens (第 1 代) 模擬器，您必須取消選取 VS 範本，然後[從 Visual Studio Marketplace 加以安裝](https://marketplace.visualstudio.com/items?itemName=WindowsMixedRealityteam.WindowsMixedRealityAppTemplatesVSIX)。 |

## <a name="install-your-engine-of-choice"></a>安裝您選擇的引擎

現在您已準備好 Windows 10、Visual Studio 和 Windows 10 SDK，讓我們安裝並設定您所選擇的引擎。 

如果您仍然需要選擇引擎，請參閱 [混合現實開發的簡介](./development.md?tabs=unity#what-technology-path-are-you-interested-in)。 

[!INCLUDE[](includes/tools-overview.md)]