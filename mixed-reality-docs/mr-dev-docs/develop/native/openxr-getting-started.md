---
title: 開始使用 OpenXR
description: 開始使用 Windows Mixed Reality 上的便攜 OpenXR API 標準，並 HoloLens 2 耳機。
author: thetuvix
ms.author: alexturn
ms.date: 2/28/2020
ms.topic: article
keywords: OpenXR、Khronos、BasicXRApp、Windows Mixed Reality、OpenXR 開發人員工具、DirectX、原生、原生應用程式、自訂引擎、中介軟體、使用者入門、101、預覽延伸模組、OpenXR 執行階段版本、系統狀態
ms.openlocfilehash: 918dfb1f336598548735b1699c61d1b350fed293
ms.sourcegitcommit: 2bf79eef6a9b845494484f458443ef4f89d7efc0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/17/2020
ms.locfileid: "97613192"
---
# <a name="getting-started-with-openxr"></a>開始使用 OpenXR

您可以在 HoloLens 2 上使用 OpenXR 或在電腦上使用 Windows Mixed Reality 沉浸式頭戴裝置進行開發。  如果您沒有耳機的存取權，您可以改用 HoloLens 2 模擬器或 Windows Mixed Reality 模擬器。

## <a name="getting-started-with-openxr-for-hololens-2"></a>開始使用 OpenXR 進行 HoloLens 2

若要開始開發 HoloLens 2 的 OpenXR 應用程式：

1. 設定 HoloLens 2 或遵循指示來 [安裝最新版本的 HoloLens 2 模擬器](../platform-capabilities-and-apis/using-the-hololens-emulator.md)。 如果您使用的是最新的模擬器映射，或裝置已更新其 OS，您應該已有 OpenXR 1.0 準備就緒可供使用。
2. 從裝置或模擬器啟動 **Store** 應用程式，以確定您已取得最新的 OpenXR 執行時間，並提供所有 [延伸](openxr.md#roadmap)模組。
    * 開啟右上方的功能表，選取 [ **下載和更新**]，然後選擇 [ **取得更新**]。  

> [!NOTE]
> 如果您使用模擬器，模擬器映射會在您每次啟動時重設，因此最好是確定您有 [最新版的 HoloLens 2 模擬器映射](../platform-capabilities-and-apis/using-the-hololens-emulator.md)。

## <a name="getting-started-with-openxr-for-windows-mixed-reality-headsets"></a>開始使用適用于 Windows Mixed Reality 耳機的 OpenXR

若要開始開發適用于沉浸式 Windows Mixed Reality 耳機的 OpenXR 應用程式：

1. 請確定您至少執行 (1903) 的 Windows 10 2019 年5月更新，這是 Windows Mixed Reality 終端使用者執行 OpenXR 應用程式的最低需求。  如果您使用的是舊版的 Windows 10，您可以使用 <a href="https://www.microsoft.com/software-download/windows10" target="_blank">Windows 10 更新助理</a>進行升級。
2. 設定 Windows Mixed Reality 耳機或遵循指示來 [啟用 Windows Mixed Reality](../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md)模擬器。

這樣就完成了！  系統會為所有 Windows Mixed Reality 使用者安裝 Windows Mixed Reality OpenXR 執行時間，並自動使其成為作用中狀態。  Microsoft Store 接著會讓執行時間保持在最新狀態。

若要再次啟用 Windows Mixed Reality OpenXR 執行時間，請從 [開始] 功能表啟動混合實境入口，然後選取視窗頂端的 [修正]。  如果該按鈕遺失，表示 OpenXR 執行時間已在使用中。<br>

## <a name="getting-the-openxr-developer-tools-for-windows-mixed-reality"></a>取得 Windows Mixed Reality 的 OpenXR 開發人員工具

若要試用 Windows Mixed Reality OpenXR 執行時間，您可以安裝 <a href="https://www.microsoft.com/store/productId/9n5cvvl23qbt" target="_blank">OpenXR Developer Tools for Windows Mixed Reality 應用程式</a>。  此應用程式提供各種 OpenXR 功能的示範，以及具有使用中執行時間和目前耳機相關重要資訊的系統狀態頁面。

使用 HoloLens 2 模擬器時，安裝適用于 Windows Mixed Reality 的 OpenXR 開發人員工具最簡單的方式是透過 [Windows 裝置入口網站](../platform-capabilities-and-apis/using-the-windows-device-portal.md)。 流覽至 [OpenXR] 頁面，然後按一下 [開發人員功能] 下的 [安裝] 按鈕，該按鈕也可在實體 HoloLens 2 裝置上運作。

![適用于 Windows Mixed Reality 應用程式的 OpenXR 開發人員工具](images/mixed-reality-openxr-developer-tools.png)

## <a name="building-a-sample-openxr-app"></a>建立範例 OpenXR 應用程式

如果尚未安裝 OpenXR 開發所需的工具，請務必 [安裝這些工具](../install-the-tools.md) 。

<a href="https://github.com/microsoft/OpenXR-MixedReality/tree/master/samples/BasicXrApp" target="_blank">BasicXrApp</a>專案會顯示一個簡單的 OpenXR 範例，其中包含 WIN32 和 UWP HoloLens 2 專案檔 Visual Studio。 因為解決方案包含 HoloLens UWP 專案，所以您需要在 Visual Studio 中安裝 [通用 Windows 平臺開發工作負載](../install-the-tools.md#installation-checklist) ，才能完全開啟。

由於封裝和部署的差異，Win32 和 UWP 專案檔是分開的，因此每個專案內的應用程式程式碼幾乎完全相同！

建立 OpenXR Win32 desktop 之後。EXE，您可以在任何支援 OpenXR 的 desktop VR 平臺上搭配 VR 耳機使用它，無論耳機類型為何。

建立 OpenXR UWP 應用程式套件之後，您可以將 [該套件部署](../platform-capabilities-and-apis/using-visual-studio.md) 到 HoloLens 2 裝置或 HoloLens 2 模擬器。

## <a name="learning-the-openxr-api"></a>學習 OpenXR API

如需 OpenXR API 的導覽，請參閱 Visual Studio 中的這段60分鐘影片 <a href="https://github.com/microsoft/OpenXR-MixedReality/tree/master/samples/BasicXrApp" target="_blank">BasicXrApp</a> 範例。  影片會示範如何在您自己的引擎中使用 OpenXR API 的每個主要元件，也會示範現今建置於 OpenXR 上的一些應用程式：

>[!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/OpenXR-Cross-platform-native-mixed-reality/player?format=ny]

## <a name="integrate-the-openxr-loader-into-a-project"></a>將 OpenXR 載入器整合至專案

若要在現有專案中開始使用 OpenXR，您將包含 OpenXR 載入器。  載入器會探索裝置上的作用中 OpenXR 執行時間，並提供其所執行之核心函式和擴充功能的存取權。

您可以從 Visual Studio 專案 [參考官方的 OpenXR NuGet 套件](#reference-official-openxr-nuget-package) ，或從 Khronos GitHub 存放庫 [包含官方 OpenXR 載入器來源](#include-official-openxr-loader-source) 。  這兩種方法都可讓您存取 OpenXR 1.0 核心功能，以及已發佈 `KHR` `EXT` 和 `MSFT` 延伸模組。

如果您有興趣使用延伸模組進行實驗 `MSFT_preview` ，您可以從混合現實的 GitHub 存放庫 [中複製預覽 OpenXR 標頭](#using-preview-extensions) 。

### <a name="reference-official-openxr-nuget-package"></a>參考官方 OpenXR NuGet 套件

<a href="https://www.nuget.org/packages/OpenXR.Loader/" target="_blank"> **OpenXR 載入** 器 NuGet 套件</a>是參考預建 OpenXR 載入器的最簡單方式。Visual Studio c + + 方案中的 DLL。  這可讓您存取 OpenXR 1.0 核心功能，以及已發佈 `KHR` `EXT` 和 `MSFT` 延伸模組。

若要將 OpenXR 載入器 NuGet 套件參考新增至您的 Visual Studio c + + 方案：
1. 在 **方案總管** 中，以滑鼠右鍵按一下要使用 OpenXR 的專案，然後選取 [ **管理 NuGet 套件 ...**]。
2. 切換至 [ **流覽** ] 索引標籤，然後搜尋 **OpenXR 載入** 器。
3. 選取 **OpenXR 載入** 器套件，然後在右邊的詳細資料窗格中選取 [安裝]。
4. 選取 [確定] 以接受專案的變更。
5. 新增 `#include <openxr/openxr.h>` 至原始檔，以開始使用 OPENXR API。

若要查看作用中 OpenXR API 的範例，請參閱 <a href="https://github.com/microsoft/OpenXR-MixedReality/tree/master/samples/BasicXrApp" target="_blank">BasicXrApp</a> 範例應用程式。

### <a name="include-official-openxr-loader-source"></a>包含官方 OpenXR 載入器來源

如果您想要自行建立載入器，例如避免額外的載入器。DLL，您可以將官方的 Khronos OpenXR 載入器來源提取至您的專案。  這可讓您存取 OpenXR 1.0 核心功能，以及已發佈 `KHR` `EXT` 和 `MSFT` 延伸模組。

若要開始使用，請遵循 <a href="https://github.com/KhronosGroup/OpenXR-SDK" target="_blank">GitHub 上 Khronos OpenXR-SDK</a>存放庫中的指示。  專案設定為使用 CMake 建立-如果您使用 MSBuild，則必須將程式碼複製到您自己的專案中。

## <a name="using-preview-extensions"></a>使用預覽延伸模組

`MSFT_preview`[延伸模組藍圖](openxr.md#roadmap)中所列的延伸模組是為了收集意見反應而預覽的實驗廠商擴充功能。  這些延伸模組僅適用于開發人員裝置，並會在真正的延伸模組發行時移除。

如果您想要試用可用的擴充功能 `MSFT_preview` ，請執行下列步驟來更新您的專案：
1. 遵循上述其中一種方法，將 OpenXR 載入器整合到您的專案中。
2. 將您專案中的標準 OpenXR 標頭取代為 <a href="https://github.com/microsoft/OpenXR-MixedReality/tree/master/openxr_preview/include/openxr" target="_blank">GitHub 上 Mixed Reality OpenXR</a>存放庫中的預覽標頭。

若要在目標 HoloLens 2 或桌上型電腦上啟用預覽延伸模組支援：
  1. 若要確定您有最新的 OpenXR 執行時間，並顯示所有 [延伸](openxr.md#roadmap) 模組，請從目標裝置或模擬器內啟動 **Store** 應用程式，開啟右上方的功能表，選取 [ **下載和更新** ]，然後選擇 [ **取得更新**]。
  2. 從 Microsoft Store 將 <a href="https://www.microsoft.com/store/productId/9n5cvvl23qbt" target="_blank">Windows Mixed Reality 應用程式的 OpenXR 開發人員工具</a> 安裝到目標裝置，然後執行它。
  3. 流覽至 [ **開發人員設定** ] 索引標籤，然後啟用 [ **使用最新 preview OpenXR 運行** 時間]  這會啟用您裝置上已啟用預覽延伸模組的預覽執行時間。
     ![OpenXR Developer Tools for Windows Mixed Reality app Developer Settings] 索引標籤](images/mixed-reality-openxr-developer-tools-settings.png)
  4. 確認 [OpenXR Developer Tools for Windows Mixed Reality](openxr-getting-started.md#getting-the-openxr-developer-tools-for-windows-mixed-reality)的 [**系統狀態**] 索引標籤上所顯示的 **執行階段版本**，符合您打算嘗試的預覽擴充功能所需的版本。  若是如此，您應該會在 [ **擴充** 功能] 清單中看到延伸模組。  一旦穩定的擴充功能可供使用，將會移除其預覽延伸模組。<br />
     ![OpenXR 開發人員工具以 Windows Mixed Reality 應用程式系統狀態] 索引標籤](images/mixed-reality-openxr-developer-tools-status.png)

如需這些預覽延伸模組的檔和使用方式的範例，請參閱 <a href="https://github.com/microsoft/OpenXR-MixedReality#openxr-preview-extensions" target="_blank">Mixed Reality OpenXR</a> 存放庫。

## <a name="troubleshooting"></a>疑難排解

如果您在進行 OpenXR 開發時遇到問題，請參閱我們的 [疑難排解秘訣](openxr-troubleshooting.md)。