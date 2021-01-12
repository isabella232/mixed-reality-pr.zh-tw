---
title: 1. 開始使用
description: 教學課程系列的第 1 部分 (共有 6 部分)，使用 Unreal Engine 4 和混合實境工具組 UX 工具外掛程式來建置國際象棋應用程式
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 混合實境, 教學課程, 開始使用, mrtk, uxt, UX 工具, 文件, 混合實境頭戴式裝置, windows 混合實境頭戴式裝置, 虛擬實境頭戴式裝置
ms.openlocfilehash: 762247f550a3471bbbb6d1004283c6f901346503
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2021
ms.locfileid: "98009788"
---
# <a name="1-getting-started"></a>1.開始使用

無論您是混合實境的新手還是經驗豐富的專業人員，都可以從此處開始體驗 [HoloLens 2](https://docs.microsoft.com/windows/mixed-reality/) 和 [Unreal Engine](https://www.unrealengine.com/en-US/)。 本教學課程系列將提供逐步指南，說明如何使用 [UX 工具外掛程式](https://github.com/microsoft/MixedReality-UXTools-Unreal)建立互動式的國際象棋應用程式 - 這是[適用於 Unreal 的混合實境工具組](https://github.com/microsoft/MixedRealityToolkit-Unreal)的一部分。 此外掛程式可協助您使用程式碼、藍圖和範例，將常用的 UX 功能新增至您的專案。 

![檢視區中的最終場景](images/unreal-uxt/5-endscene.PNG)

在系列結束時，您將擁有以下方面的體驗：
* 開始新專案
* 設定混合實境
* 處理使用者輸入
* 新增按鈕
* 在模擬器或裝置上播放

## <a name="prerequisites"></a>必要條件

在進行之前，請確定您已安裝下列項目：
* Windows 10 1809 或更新版本
* Windows 10 SDK 10.0.18362.0 或更新版本
* [Unreal Engine](https://www.unrealengine.com/en-US/get-now) 4.25 或更新版本
* [針對開發而設定](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)的 Microsoft HoloLens 2 裝置或[模擬器](../../platform-capabilities-and-apis/using-the-hololens-emulator.md#hololens-2-emulator-overview)
* Visual Studio 2019 與下列工作負載

### <a name="installing-visual-studio-2019"></a>安裝 Visual Studio 2019

首先，請確定您的設定具有所有必要的 Visual Studio 套件：
1. 安裝最新版 [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/)
1. 安裝下列[工作負載](https://docs.microsoft.com/visualstudio/install/modify-visual-studio?#modify-workloads)：
    * 使用 C++ 的傳統型開發
    * .NET 桌面開發
    * 通用 Windows 平台開發
1. 展開「通用 Windows 平台開發」，然後選取： 
    * USB 裝置連線
    * C++ (v142) 通用 Windows 平台工具

1. 安裝下列[元件](https://docs.microsoft.com/visualstudio/install/modify-visual-studio?#modify-individual-components)：
    * 編譯器、建置工具與執行階段 > MSVC v142 - VS 2019 C++ ARM64 建置工具 (最新版本)

您可以使用下列圖片來確認安裝

![VS 安裝程式中的重要刻度](images/unreal-uxt/1-install-the-tools.png)

這樣就完成了！ 您已準備好繼續著手進行國際象棋專案。

[下一節：2.初始化您的專案和第一個應用程式](unreal-uxt-ch2.md)