---
title: 匯出和建置 Unity Visual Studio 解決方案
description: 本文概述如何從 Unity 匯出您的混合現實專案，讓您可以在 Visual Studio 中建立和部署。
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: unity、visual studio、匯出、組建、部署、HoloLens、混合現實耳機、windows mixed reality 耳機、虛擬實境耳機、UWP、部署
ms.openlocfilehash: 29415fa7d561cab1aec5f0c2c9344fa24b0e8293
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/17/2020
ms.locfileid: "94677557"
---
# <a name="exporting-and-building-a-unity-visual-studio-solution"></a>匯出和建置 Unity Visual Studio 解決方案

如果您不打算在應用程式中使用系統鍵盤，我們的建議是使用 *D3D* ，因為您的應用程式會使用較少的記憶體，而且啟動時間會稍微快一點。 如果您在專案中使用 TouchScreenKeyboard API 來使用系統鍵盤，您需要將它匯出為 *XAML*。

## <a name="how-to-export-from-unity"></a>如何從 Unity 匯出

![Unity 組建設定](images/unitybuildsettings-300px.png)<br>
*Unity 組建設定*

1. 當您準備好從 Unity 匯出專案時，請 **開啟 [檔案**] 功能表，然後選取 [**組建設定 ...** ]。
2. 按一下 [ **新增開啟的場景** ]，將您的場景加入組建中。
3. 在 [ **組建設定** ] 對話方塊中，選擇下列選項以匯出 HoloLens：
   * **平臺：** *通用 Windows 平臺* 並務必選取 [ **切換平臺** ]，讓您的選擇生效。
   * **SDK：** *通用 10*。
   * **UWP 組建類型：** *D3D*。
4. **選用**： **Unity c # 專案：** 已核取。

>[!NOTE]
>勾選此方塊可讓您：
>* 在 Visual Studio 遠端偵錯程式中，為您的應用程式進行偵錯工具。
>* 使用 IntelliSense 進行 WinRT Api 時，請編輯 Unity c # 專案中的腳本。

5. 從 [**組建設定 ...** ] 視窗中，開啟 [**播放玩家設定**]。
6. 選取 [ **通用 Windows 平臺** ] 索引標籤的設定。
7. 展開 [XR 設定] 群組。
8. 在 [ **XR 設定** ] 區段中，核取 [ **支援虛擬事實** ] 核取方塊以新增 **虛擬實境裝置** 清單，並確認 **[Windows Mixed Reality]** 列為支援的裝置。
9. 返回 [ **組建設定** ] 對話方塊。
10. 選取 [組建]  。
11. 在出現的 [Windows 檔案總管] 對話方塊中，建立新的資料夾來保存 Unity 的組建輸出。 一般來說，我們會將資料夾命名為 "App"。
12. 選取新建立的資料夾，然後按一下 [ **選取資料夾**]。
13. Unity 完成建立之後，會開啟專案根目錄的 Windows 檔案總管視窗。 流覽至新建立的資料夾。
14. 開啟位於此資料夾內產生的 Visual Studio 方案檔。

## <a name="when-to-re-export-from-unity"></a>從 Unity 重新匯出的時機

從 Unity 匯出您的應用程式時，核取 [c # 專案] 核取方塊會建立包含所有 Unity 腳本檔案的 Visual Studio 方案。 這可讓您逐一查看腳本，而不需要從 Unity 重新匯出。 但是，如果您想要對專案進行變更，而不只是變更腳本的內容，您必須從 Unity 重新匯出。 您需要從 Unity 重新匯出的一些時間範例如下：
* 您可以在 [專案] 索引標籤中新增或移除資產。
* 您可以在 [偵測器] 索引標籤中變更任何值。
* 您可以從 [階層] 索引標籤新增或移除物件。
* 您變更任何 Unity 專案設定

## <a name="building-and-deploying-a-unity-visual-studio-solution"></a>建立及部署 Unity Visual Studio 解決方案

建立和部署應用程式的其餘部分會在 [Visual Studio](../platform-capabilities-and-apis/using-visual-studio.md)中進行。 您將需要指定 Unity 組建設定。 Unity 的命名慣例可能與您在 Visual Studio 中經常用到的不同：

|  設定  |  說明 | 
|----------|----------|
|  偵錯  |  關閉所有優化，並啟用分析工具。 用來對腳本進行調試。 | 
|  Master  |  所有優化都會開啟，並停用分析工具。 用來將應用程式提交到存放區。 | 
|  版本  |  所有優化都已開啟，並且已啟用分析工具。 用來評估應用程式效能。 | 

請注意，上述清單是常見觸發程式的子集，這些觸發程式會導致 Visual Studio 專案需要產生。 一般而言，從 Visual Studio 中編輯 .cs 檔案不需要從 Unity 內重新產生專案。

## <a name="troubleshooting"></a>疑難排解

如果您在 Visual Studio 專案中發現無法辨識 .cs 檔案的編輯，請確定當您從 Unity 的 [組建] 功能表產生 VS 專案時，已核取 [Unity c # 專案]。
