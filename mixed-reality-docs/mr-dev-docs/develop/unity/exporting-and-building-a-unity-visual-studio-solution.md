---
title: 匯出和建置 Unity Visual Studio 解決方案
description: 本文概述如何從 Unity 匯出您的混合現實專案，讓您可以在 Visual Studio 中建立和部署。
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: unity、visual studio、匯出、組建、部署、HoloLens、混合現實耳機、windows mixed reality 耳機、虛擬實境耳機、UWP、部署
ms.openlocfilehash: 78410da352b1cce1377b35737376437608f3017c00334c1a489ede26d5170d2d
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2021
ms.locfileid: "115203603"
---
# <a name="exporting-and-building-a-unity-visual-studio-solution"></a>匯出和建置 Unity Visual Studio 解決方案

如果您的應用程式不需要系統鍵盤，我們的建議是使用 *D3D* ，讓您的應用程式使用較少的記憶體，並縮短啟動時間。 不過，如果您是透過 TouchScreenKeyboard API 使用系統鍵盤，您需要將專案匯出為 *XAML*。

## <a name="how-to-export-from-unity"></a>如何從 Unity 匯出

![Unity 組建設定](images/unitybuildsettings-300px.png)<br>
*Unity 編輯器中的組建設定*

1. 當您準備好從 Unity 匯出專案時，請 **開啟 [檔案**] 功能表，然後選取 [**組建設定**]。
2. 選取 [ **新增開啟的場景** ]，將您的場景新增至組建。
3. 在 [**組建設定**] 對話方塊中，選擇要匯出 HoloLens 的下列選項：
   * **平臺：** *通用 Windows 平臺* 並務必選取 [**切換平臺**]，讓您的選擇生效。
   * **SDK：** *通用 10*。
   * **UWP 組建類型：** *D3D*。
4. **選用**： **Unity c # 專案：** 已核取。

>[!NOTE]
>勾選此方塊可讓您：
>* 在 Visual Studio 遠端偵錯程式中，為您的應用程式進行偵錯工具。
>* 使用 IntelliSense 進行 WinRT Api 時，請編輯 Unity c # 專案中的腳本。

5. 從 [**組建設定**] 視窗中，開啟 [**播放設定 ...** ]
6. 選取 [**通用 Windows 平臺**] 索引標籤的 [設定]。
7. 展開 [XR 設定] 群組。
8. 在 [ **XR 設定**] 區段中，核取 [**支援虛擬實境**] 核取方塊以新增 **虛擬實境裝置** 清單，並確認 **[Windows Mixed Reality]** 列為支援的裝置。
9. 返回 [**組建設定**] 對話方塊。
10. 選取 [組建]  。
11. 在出現的 [Windows 檔案總管] 對話方塊中，建立新的資料夾來保存 Unity 的組建輸出。 一般來說，我們會將資料夾命名為 "App"。
12. 選取新建立的資料夾，然後選取 [ **選取資料夾**]。
13. Unity 完成建立之後，會開啟專案根目錄的 Windows 檔案總管視窗。 流覽至新建立的資料夾。
14. 開啟位於此資料夾內產生的 Visual Studio 方案檔。

## <a name="when-to-re-export-from-unity"></a>從 Unity 重新匯出的時機

從 unity 匯出您的應用程式時，檢查 **c # 專案** 核取方塊會建立包含所有 Unity 腳本檔案的 Visual Studio 解決方案。 將您的所有腳本都放在一個位置，可讓您逐一查看，而不需要從 Unity 重新匯出。 但是，如果您對專案進行變更，而不只是變更腳本的內容，您必須從 Unity 重新匯出。 您需要從 Unity 重新匯出的一些時間範例如下：
* 您可以在 [Project] 索引標籤中新增或移除資產。
* 您可以在 [偵測器] 索引標籤中變更任何值。
* 您可以從 [階層] 索引標籤新增或移除物件。
* 您變更任何 Unity 專案設定

## <a name="building-and-deploying-a-unity-visual-studio-solution"></a>建立及部署 Unity Visual Studio 解決方案

建立和部署應用程式的其餘部分會在[Visual Studio](../platform-capabilities-and-apis/using-visual-studio.md)中進行。 您將需要指定 Unity 組建設定。 Unity 的命名慣例可能與您在 Visual Studio 中使用的不同：

|  組態  |  說明 | 
|----------|----------|
|  偵錯  |  關閉所有優化，並啟用分析工具。 用來對腳本進行調試。 | 
|  Master  |  所有優化都會開啟，並停用分析工具。 用來將應用程式提交到存放區。 | 
|  版本  |  所有優化都已開啟，並且已啟用分析工具。 用來評估應用程式效能。 | 

請注意，上述清單是常見觸發程式的子集，這些觸發程式會導致 Visual Studio 專案需要產生。 一般而言，從 Visual Studio 中編輯 .cs 檔案不需要從 Unity 內重新產生專案。

## <a name="troubleshooting"></a>疑難排解

如果您在 Visual Studio 專案中發現無法辨識 .cs 檔案的編輯，請確定當您從 unity 的 [組建] 功能表產生 VS 專案時，會檢查 **Unity c # 專案**。
