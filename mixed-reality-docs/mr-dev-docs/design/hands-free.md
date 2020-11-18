---
title: 免持式
description: 深入瞭解使用者可能會面對的手入控制器介面，以及各種免參與的替代方案。
author: hferrone
ms.author: v-hferrone
ms.date: 04/20/2019
ms.topic: article
keywords: Mixed Reality、免持手、注視、注視目標、互動、設計、混合現實耳機、windows mixed Reality 耳機、虛擬實境耳機、HoloLens、MRTK、混合現實工具組、語音輸入、可用性
ms.openlocfilehash: 7f4d3a0ec8d2e7435f54164006a8bd122b1ebcba
ms.sourcegitcommit: 4f3ef057a285be2e260615e5d6c41f00d15d08f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/17/2020
ms.locfileid: "94702134"
---
# <a name="hands-free"></a>免持式

## <a name="scenarios"></a>案例

如 [互動模型](interaction-fundamentals.md)中所述，當您識別出使用者及其目標之後，請自問他們在完成其工作時可能面臨的環境或環境問題。 例如，許多使用者都必須使用他們的手來完成其真實世界的目標，而這些使用者將難以與以操作站為基礎的介面互動。 

部分特定案例包括： 
* 當使用者的雙手忙碌時，可利用引導來完成工作
* 當使用者的雙手忙碌時參考資料
* 手部疲勞
* 無法追蹤的手套
* 手拿東西
* 執行大型手勢的社交 awkwardness
* 空間狹窄


## <a name="hands-free-modalities"></a>免手形式

### <a name="voice-input"></a>[語音輸入](voice-input.md)

使用您的語音來命令和控制介面可提供便利的方式來操作無人參與，並可在需要時使用快速鍵來彈性略過多個步驟。 使用語音輸入時，使用者可以直接讀取任何按鈕的名稱來啟用它 ( 「 _查看它」 )_ 並與可為您完成工作的數位代理程式交談。


### <a name="gaze-and-dwell"></a>[目光和停駐](gaze-and-dwell.md)

在某些免操作的情況下，使用您的聲音並非理想或甚至可能。 很高的工廠環境、隱私權或社會規範都可以是條件約束。 「注視 + 停留」模型可讓使用者在沒有任何額外輸入的情況下，流覽應用程式，而不需要任何額外的輸入，因為使用者只會在目標上保持撥雲見日)  (，並 lingers 一段時間來啟用它。 若要深入瞭解「注視 + 停留」的個別設計考慮，請查看 [眼睛](gaze-and-dwell-eyes.md) 和中的眼睛 [+ 停留](gaze-and-dwell-head.md)。


## <a name="transitioning-in-and-out-of-hands-free"></a>無人參與的轉換

在這些情況下，讓您的手與可進行命令和流覽的全像投影互動，可能是從端對端操作應用程式的絕對需求，一直到使用者可以隨時轉換的額外便利性。 

如果應用程式的需求是永遠免費使用，不論是使用停留、自訂語音命令或單一語音命令「選取」，然後務必在您的 UI 中製作適當的住宿。 

如果您的目標使用者需要自行決定是否可自由地切換，請務必將下列準則納入考慮。

### <a name="assume-the-user-is-already-in-the-mode-that-they-want-to-switch-to"></a>假設使用者已經處於想要切換的模式
比方說，如果使用者是在工廠，在 HoloLens 上觀賞影片參考，並決定挑選扳手以開始工作，她最有可能開始操作，而不需要減少扳手來按下按鈕。 她應該能夠使用語音命令來叫用語音會話、停留在已可見的 UI 上以開始停留，或說「select」這個字。

使用者應該能夠： 
* 無人參與，請切換為無人參與
* 改用您的手
* 使用控制器切換至控制器 

### <a name="create-redundant-ways-to-switch-modes"></a>建立切換模式的重複方式
第一個原則是關於存取權，第二個原則是關於可用性。 您不應該只是在模式中進行轉換的單一方法。 

以下是一些範例： 
* 開始語音互動的按鈕
* 要轉換成的聲音命令，使用前端和停留

### <a name="add-a-dash-of-drama"></a>新增戲劇的虛線
模式切換是很重要的一件事，就是當這些轉換發生明確（甚至是很大的參數）時，讓使用者知道發生什麼事。 


## <a name="usability-checklist"></a>可用性檢查清單

**使用者是否可以進行任何動作，而不需要端對端？**
* 每個互動都應該可無人參與
* 確定所有的自訂手勢都有取代，例如調整大小、放置、撥動、點擊等。
* 確保使用者隨時都能安心控制 UI 的出現、放置和詳細資訊
    * 無法取得 UI
    * 將不在視野內的 UI 定址 (FOV) 
    * 我看到的是多少，哪裡

**使用正確的 affordances 來教授和加強互動的機制？**

使用者是否瞭解 .。。
* ...它們在哪個模式中？
* ...在此模式中可以怎麼做？
* ...目前的狀態為何？
* ...如何進行轉換？
    
**UI 是否已針對無人參與優化？**   

* 範例：停留 affordances 並非內建至一般2D 模式
* 範例：使用物件反白顯示時，語音目標更好
* 範例：語音互動優於需要開啟的標題


## <a name="see-also"></a>另請參閱
* [HoloLens 2 的眼球追蹤](eye-tracking.md)
* [目光和行動](gaze-and-commit.md)
* [目光和停駐](gaze-and-dwell.md)
* [手 - 直接操作](direct-manipulation.md)
* [手 - 手勢](gaze-and-commit.md#composite-gestures)
* [手 - 指向和行動](point-and-commit.md)
* [本能互動](interaction-fundamentals.md)
* [語音輸入](voice-input.md)
