---
title: 新增本機語音轉換文字翻譯離線模式
description: 完成此課程，以了解如何在混合實境應用程式中新增離線模式以進行本機語音轉換文字翻譯。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens, MRTK, 混合實境工具組, UWP, Azure 空間錨點, 語音辨識, Windows 10
ms.localizationpriority: high
ms.openlocfilehash: 2e7a48dc4bb64eb177e6fa290f4918345c3d642f
ms.sourcegitcommit: 68140e9ce84e69a99c2b3d970c7b8f2927a7fc93
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/05/2021
ms.locfileid: "99590150"
---
# <a name="2-adding-an-offline-mode-for-local-speech-to-text-translation"></a>2.新增本機語音轉換文字翻譯離線模式

在本教學課程中，您將新增使用 Azure 語音辨識執行命令的功能，這可讓您根據所定義的單字或片語進行一些動作。

## <a name="objectives"></a>目標

* 了解如何使用 Azure 語音辨識來執行命令

## <a name="instructions"></a>指示

在 [階層] 視窗中選取 **Lunarcom** 物件，然後在 [偵測器] 視窗中使用 [新增元件] 按鈕來將 **Lunarcom Wake Word Recognizer (指令碼)** 元件新增至 Lunarcom 物件，並進行以下設定：

* 在 [喚醒字詞] 欄位中，入適當的片語，例如「啟動終端機 (Activate terminal)」。
* 在 [關閉字詞] 欄位中，輸入適當的片語，例如「關閉終端機 (Dismiss terminal)」。

![已醒目提示 Lunarcom Wake Word Recognizer 指令碼元件的 Unity 編輯器](images/mrlearning-speech/tutorial2-section1-step1-1.png)

> [!NOTE]
> Lunarcom Wake Word Recognizer (指令碼) 元件不是 MRTK 的一部分。 這是本教學課程資產隨附的元件。

如果您現在進入遊戲模式，如先前的教學課程所示，預設會啟用終端機面板，但您現在可以藉由說出關閉字詞：**關閉終端機**，來將其停用：

![在播放模式中使用語音辨識器功能的 Unity 編輯器](images/mrlearning-speech/tutorial2-section1-step1-2.png)

然後藉由說出喚醒字詞：**啟動終端機**，來再次將其啟動：

![在播放模式中具有作用中終端機的 Unity 編輯器](images/mrlearning-speech/tutorial2-section1-step1-3.png)

> [!CAUTION]
> 應用程式必須連線到 Azure，因此請確定您的電腦/裝置已連線到網際網路。

> [!TIP]
> 如果您預期無法經常連線到 Azure，您也可以遵循[使用語音命令](mr-learning-base-09.md)指示，使用 MRTK 來實作語音命令。

## <a name="congratulations"></a>恭喜！

您已實作由 Azure 提供技術支援的語音命令。 在您的裝置上執行應用程式，以確保功能可正常運作。

在下一個教學課程中，您將了解如何使用 Azure 語音翻譯來轉譯語音。

> [!div class="nextstepaction"]
> [下一個教學課程：3.新增 Azure 認知服務語音翻譯元件](mrlearning-speechSDK-ch3.md)
