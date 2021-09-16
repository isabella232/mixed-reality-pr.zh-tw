---
title: 使用 Visual Studio 來部署和偵錯
description: 了解如何使用 Visual Studio 來建置、偵錯及部署 HoloLens 和 Windows Mixed Reality 的應用程式。
author: pbarnettms
ms.author: pbarnett
ms.date: 09/15/2021
ms.topic: article
ms.localizationpriority: high
keywords: Visual Studio, HoloLens, 混合實境, 偵錯, 部署
ms.openlocfilehash: 948ec52dcfe738a28316e9906d473b32454f6d59
ms.sourcegitcommit: 7dad5bde71d429bb23c72a4074e60b6668a7f091
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/16/2021
ms.locfileid: "127857501"
---
# <a name="using-visual-studio-to-deploy-and-debug"></a>使用 Visual Studio 來部署和偵錯

無論您是使用 DirectX 或 Unity 來開發混合實境應用程式，Visual Studio 都是進行偵錯和部署的必備工具。 在本節中，您將了解如何：
* 透過 Visual Studio 將應用程式部署到 HoloLens 或 Windows Mixed Reality 沉浸式頭戴裝置。
* 使用內建至 Visual Studio 的 HoloLens 模擬器。
* 針對混合實境應用程式進行偵錯。

## <a name="prerequisites"></a>必要條件

1. 如需安裝指示，請參閱[安裝工具](../../develop/install-the-tools.md#installation-checklist)。
2. 在 Visual Studio 中建立新的通用 Windows app 專案。  對於 HoloLens (第 1 代)，使用 Visual Studio 2017 或更新版本。  對於 HoloLens 2，使用 Visual Studio 2019 16.2 或更新版本。 支援 C# 和 C++。 (或者遵循指示，[在 Unity 中建立應用程式](../../develop/unity/tutorials/holograms-100.md)。)

## <a name="enabling-developer-mode"></a>啟用開發人員模式

從在您的裝置上啟用 **開發人員模式** 開始，讓 Visual Studio 可以與它連線。

### <a name="hololens"></a>HoloLens

1. 開啟您的 HoloLens 並將裝置戴上。
2. 使用[開始手勢](../../design/system-gesture.md)來啟動主功能表。
3. 選取 [設定]  磚，在您的環境中啟動應用程式。
4. 選取 [更新]  功能表項目。
5. 選取 [適用於開發人員]  功能表項目。
6. 啟用 [**使用開發人員功能**]，將應用程式從 Visual Studio 部署至您的 HoloLens。 如果您的裝置正在執行 Windows 全像21H1 版或更新版本，則也會啟用 **裝置探索**。
7. 選擇性：向下捲動而且啟用 [裝置入口網站]，可讓您從網頁瀏覽器連線到您 HoloLens 上的 [Windows 裝置入口網站](using-the-windows-device-portal.md)。

### <a name="windows-pc"></a>Windows PC

如果您使用的是連線到電腦的 Windows Mixed Reality 頭戴式裝置，就必須在電腦上啟用 **開發人員模式**。
1. 移至 [設定] 
2. 選取 [更新與安全性] 
3. 選取 [適用於開發人員] 
4. 啟用 [開發人員模式]，閱讀您所選設定的免責聲明，然後選取 [是] 來接受變更。

## <a name="deploying-a-hololens-app-over-wi-fi"></a>透過 Wi-Fi 部署 HoloLens 應用程式 

使用下列屬性來設定您的 Visual Studio 專案：

1. 選取您的應用程式編譯選項
    * 針對 Unity 專案，選擇 [**發行**] 或 [**主要**] 
    * 針對所有其他專案，選擇 [**發行**]

> [!NOTE]
> 您可以在[匯出和建立 Visual Studio 方案](../unity/exporting-and-building-a-unity-visual-studio-solution.md#building-and-deploying-a-unity-visual-studio-solution)中，找到每個編譯選項的完整定義。

2. 根據您的裝置選取組建設定

[!INCLUDE[](includes/vs-wifi-hl-include.md)]

3. 在 [部署目標] 下拉式功能表中，選取 [遠端電腦] 

![Visual Studio 中的遠端電腦部署目標](images/remotemachinesetting_arm64.png)

接下來，您需要設定遠端連線。 針對 C++ 和 JavaScript 專案，請移至 [專案 > 屬性 > 設定屬性 > 偵錯]  。 如果您是在 c # 專案中工作，對話方塊應該會自動出現。

> [!NOTE]
> 如果 [遠端連線] 對話方塊未出現在 c # 專案中，您可以從 [ **屬性] > Debug**] 手動開啟。

1. 在 [位址]  或 [電腦名稱]  欄位中，輸入您裝置的 IP 位址。 
    * 您可以在 HoloLens **設定 > Network & Internet > Advanced Options** 下的找到 IP 位址
    * 我們一律建議以手動方式輸入您的 IP 位址，而不是根據自動偵測到的功能。

2. 將 **驗證模式** 設定為 **通用 (未加密的通訊協定)**

  ![Visual Studio 中的遠端連線對話方塊](images/remotedeploy.png)

3. 根據您的需求來建立、部署及偵測您的應用程式
    * 選取 [偵錯 > 開始偵錯]  來部署您的應用程式並開始偵錯
    * 選取 **組建 > 部署** 以在不進行調試的情況下進行組建和部署

![在 Visual Studio 中開始但不進行偵錯](images/deploywithdebugging.png)

4. 當您第一次從電腦將應用程式部署到 HoloLens 時，系統會提示您輸入 PIN 碼。 遵循以下的 **配對您的裝置** 指示。

## <a name="deploying-a-hololens-app-over-usb"></a>透過 USB 部署 HoloLens 應用程式 

<br>

>[!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Deploying-your-HoloLens-2-application/player?format=ny]

1. 選取您的應用程式編譯選項
    * 針對 Unity 專案，選擇 [**發行**] 或 [**主要**] 
    * 針對所有其他專案，選擇 [**發行**]

> [!NOTE]
> 您可以在[匯出和建立 Visual Studio 方案](../unity/exporting-and-building-a-unity-visual-studio-solution.md#building-and-deploying-a-unity-visual-studio-solution)中，找到每個編譯選項的完整定義。

2. 根據您的裝置選取組建設定

[!INCLUDE[](includes/vs-wifi-hl-include.md)]

3. 在 [部署目標] 下拉式功能表中，選取 [裝置] 

![Visual Studio 中的裝置部署](images/buildsettingsusbdeploy_arm64.png)

4. 根據您的需求來建立、部署及偵測您的應用程式
    * 選取 [偵錯 > 開始偵錯]  來部署您的應用程式並開始偵錯
    * 選取 **組建 > 部署** 以在不進行調試的情況下進行組建和部署

![在 Visual Studio 中開始但不進行偵錯](images/deploywithdebugging.png)</br>

5. 當您第一次從電腦將應用程式部署到 HoloLens 時，系統會提示您輸入 PIN 碼。 遵循以下的 **配對您的裝置** 指示。

## <a name="deploying-an-app-to-the-hololens-1st-gen-emulator"></a>將應用程式部署至 HoloLens (第 1 代) 模擬器

1. 請確定您已 **[安裝 HoloLens 模擬器](../install-the-tools.md)** 。
2. 為您的應用程式選取 **x86** 組建設定。</br>
![Visual Studio 中的 x86 組建設定](images/x86setting.png)</br>
3. 在 [部署目標] 下拉式功能表中，選取 [HoloLens 模擬器] </br>
![Visual Studio 中的模擬器目標](images/deployemulator.png)</br>
4. 選取 [偵錯 > 開始偵錯]  來部署您的應用程式並開始偵錯</br>
![在 Visual Studio 中開始但不進行偵錯](images/deploywithdebugging.png)</br>

## <a name="deploying-an-app-to-the-hololens-2-emulator"></a>將應用程式部署至 HoloLens 2 模擬器

1. 請確定您已 **[安裝 HoloLens 模擬器](../install-the-tools.md)** 。
2. 為您的應用程式選取 **x86** 或 **x64** 組建設定。</br>
![Visual Studio 中的 x86 組建設定](images/x86setting.png)</br>
3. 在 [部署目標] 下拉式功能表中，選取 [HoloLens 2 模擬器] </br>
![Visual Studio 應用程式中的 Emulator 目標](images/deployemulator2.png)</br>
4. 選取 [偵錯 > 開始偵錯]  來部署您的應用程式並開始偵錯</br>
![在 Visual Studio 中開始但不進行偵錯](images/deploywithdebugging.png)</br>

## <a name="deploying-a-vr-app-to-your-local-pc"></a>將 VR 應用程式部署到您的本機電腦 

若要使用可連線到您的電腦或[混合實境模擬器](using-the-windows-mixed-reality-simulator.md)的 Windows Mixed Reality 沉浸式頭戴裝置：
1. 為您的應用程式選取 **x86** 或 **x64** 組建設定
2. 在 [部署目標] 下拉式功能表中，選取 [本機電腦] 
3. 根據您的需求來建立、部署及偵測您的應用程式
    * 選取 [偵錯 > 開始偵錯]  來部署您的應用程式並開始偵錯
    * 選取 **組建 > 部署** 以在不進行調試的情況下進行組建和部署

## <a name="pairing-your-device"></a>配對您的裝置

當您第一次從 Visual Studio 將應用程式部署到 HoloLens 時，系統會提示您輸入 PIN 碼。 在 HoloLens 上，移至 [更新 > 適用於開發人員]，並點選 [配對]，藉由啟動 [設定] 應用程式來產生 PIN。 當您的 HoloLens 上顯示 PIN 時，請將其輸入 Visual Studio 中。 配對完成之後，點選 HoloLens 上的 [完成]  以關閉對話方塊。 這部電腦現在已與 HoloLens 配對，您可以自動部署應用程式。 針對用來將應用程式部署至 HoloLens 的每部電腦重複這些步驟。

若要解除配對您的 HoloLens 與所有配對的電腦：
* 啟動 [設定] 應用程式，移至 [更新] > [適用於開發人員]，然後點選 [清除]。

## <a name="graphics-debugger-for-hololens-1st-gen"></a>HoloLens (第 1 代) 的圖形偵錯工具

撰寫和最佳化全像攝影應用程式時，Visual Studio 圖形診斷工具很有幫助。 如需完整詳細資料，請參閱 [MSDN 上的 Visual Studio 圖形診斷](/previous-versions/visualstudio/visual-studio-2015/debugger/visual-studio-graphics-diagnostics)。

**啟動圖形偵錯工具**
1. 遵循上述指示，以裝置或模擬器為目標
2. 移至 [偵錯 > 圖形 > 開始診斷] 
3. 第一次使用 HoloLens 開始診斷時，您可能會遇到「拒絕存取」錯誤。 將 HoloLens 重新開機，讓更新的權限生效，然後再試一次。

## <a name="profiling"></a>程式碼剖析

Visual Studio 程式碼剖析工具可讓您分析應用程式的效能和資源使用。 包括將 CPU、記憶體、圖形和網路使用最佳化的工具。 如需完整詳細資料，請參閱 [MSDN 上的執行診斷工具而不進行偵錯](/previous-versions/visualstudio/visual-studio-2015/profiling/profiling-tools)。

**使用 HoloLens 啟動程式碼剖析工具**
1. 遵循上述指示，以裝置或模擬器為目標
2. 移至 [偵錯 > 啟動診斷工具但不偵錯...]  。
3. 選取您想要使用的工具
4. 選取 [啟動]
5. 第一次使用 HoloLens 開始診斷但不進行偵錯時，您可能會遇到「拒絕存取」錯誤。 將 HoloLens 重新開機，讓更新的權限生效，然後再試一次。

## <a name="debugging-an-installed-or-running-app"></a>針對已安裝或執行中的應用程式進行偵錯

您可以使用 Visual Studio 針對已安裝但未從 Visual Studio 專案部署的通用 Windows 應用程式進行偵錯。 如果您想要對已安裝的應用程式套件進行偵錯，或對已經在執行中的應用程式進行偵錯，這會很有用。
1. 移至 [偵錯 -> 其他偵錯目標 -> 針對已安裝的應用程式套件進行偵錯] 
2. 針對 HoloLens 選取 [遠端電腦]  目標，或針對沉浸式頭戴裝置選取 [本機電腦]  。
3. 輸入您裝置的 **IP 位址**
4. 選擇 [通用]  驗證模式
5. 此視窗會顯示執行中和非使用中的應用程式。 挑選您想要進行偵錯的應用程式。
6. 選擇要進行偵錯的程式碼類型 (受控、原生、混合)
7. 選取 [連結] 或 [啟動]

## <a name="next-development-checkpoint"></a>下一個開發檢查點

依循我們配置的 Unity 開發檢查點旅程，此時您會進入部署階段。 接下來，您可以繼續進行下一個主題：

> [!div class="nextstepaction"]
> [部署至 HoloLens 模擬器](using-the-hololens-emulator.md)

或者，直接跳到新增進階服務的主題：

> [!div class="nextstepaction"]
> [進階服務](../../develop/unity/unity-development-overview.md#5-adding-services)

您可以隨時回到 [Unity 開發檢查點](../../develop/unity/unity-development-overview.md#4-deploying-to-a-device-or-emulator)。

## <a name="see-also"></a>另請參閱
* [安裝工具](../install-the-tools.md)
* [使用 HoloLens 模擬器](using-the-hololens-emulator.md)
* [部署和偵錯通用 Windows 平台 (UWP) app](/windows/uwp/debug-test-perf/deploying-and-debugging-uwp-apps)
* [啟用您的裝置以進行開發](/windows/uwp/get-started/enable-your-device-for-development)
