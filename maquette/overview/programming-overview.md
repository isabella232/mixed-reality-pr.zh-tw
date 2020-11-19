---
title: 程式設計總覽
description: 瞭解如何使用腳本來存取 Maquette 物件和介面。
author: hferrone
ms.author: v-hferrone
ms.date: 10/26/2020
ms.topic: article
keywords: Windows Mixed Reality、Maquette、原型設計、混合現實、虛擬實境、VR、MR、意見反應、意見反應中樞、bug
ms.openlocfilehash: 6761ed0fab70b0d497ad1e1398cbd6c1af6ab38b
ms.sourcegitcommit: fae413a2b0420e787671af90f14ee39cde51640f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/19/2020
ms.locfileid: "94935405"
---
# <a name="programming-overview"></a>程式設計總覽

<!-- TODO(Harrison): Need consolidated logo with text -->

![標誌](../images/MaquetteIcon.png) 程式設計總覽

Microsoft Maquette 會根據 [Jint](https://github.com/sebastienros/jint) 解譯器，使用 JavaScript (ECMAScript 5.1 與延伸模組) 。 此延伸模組 `.mqjs` 是用來區別 Maquette javascript 檔案與一般 javascript。

<!-- TODO(Stefan): Need more context and high-level explanation of Maquette objects, their accessible interfaces, and functionality. 
                   - What can they do and what problems can they solve?
                   - Is there a specific link to the Maquette object API that can be included here?  
-->
Maquette 物件和介面可透過物件存取及編寫腳本 `Maquette` 。 Maquette 的 API 參考中提供 Maquette 物件和介面的相關檔。

<!-- TODO(Stefan): Link to roadmap information, which hasn't been documented yet. -->
MaquetteScript 是新的加法和 flux，因此應該要有變更。 即將提供更詳細的檔和更新。

<!-- TODO(Stefan): Is Spotlights a component or added functionality of Maquette? -->
## <a name="spotlights-on-scripting"></a>腳本的聚光燈

* TBD-以範例/教學課程為焦點的腳本編寫焦點
  * 2x 影像/標題–連結至焦點頁面

<!-- TODO(Stefan): Each of these bullets need to be fleshed out. -->
## <a name="getting-started-with-maquettescript"></a>開始使用 MaquetteScript

* Mqjs 與 .JS 的比較
* 程式設計模型
  * 編輯 vs. 正在執行
* 連結至程式設計工作流程
* 共用結果的連結

## <a name="programming-workflow"></a>程式設計工作流程

<!-- TODO(Stefan): Which of these bullets are no longer TBD? We only want to include documentation on existing content. -->
TBD
* REPL
* 腳本作業
* 偵錯工具操作
* 調試迴圈
* 複製/貼上程式碼？

## <a name="running-mqjs-scripts"></a>正在執行. mqjs 腳本

<!-- TODO(Stefan): Need screenshot -->
若要執行 MaquetteScript mqjs 檔案，請移至 Maquette 的隨附視窗，然後開啟 [腳本] 索引標籤以找出腳本。

> [!NOTE] 
> 某些選項將無法運作，因為我們尚未傳送腳本。

## <a name="vscode-editor-workflow"></a>VSCode 編輯器工作流程

若要從 VSCode 內評估 Maquette 中的腳本，使用者必須知道兩個命令：

   `CTRL-5` 評估選取的文字或游標所在的整個行。 

   `CTRL-SHIFT-5` 評估整個檔案。

<!-- TODO(Stefan): This could use a nice simple infographic of the REPL loop. -->
文字會傳送至 Maquette，並在 JavaScript 環境中進行評估，並將結果傳回至 VSCode 的輸出主控台。 這可以用來做為複寫 (讀取-評估-列印迴圈) 。

## <a name="example-first-step"></a>範例第一個步驟

<!-- TODO(Stefan): What kind of file, a C# or .mqjs file? -->
將下列程式碼複製到 VSCode 中的檔案：

```csharp
var myCube = Maquette.CreateCube();
myCube.position = Maquette.User.GetPositionInFront(0.6);
myCube.color = Color(1.0, 0.5, 0.0);
```

<!-- TODO(Stefan): Need screenshot. -->
選取程式碼，或只選取區段，然後按 [ `CTRL-5` 執行]。 這應該會建立一個 cube，將它放在您的前方，然後變更其色彩。

還有更多範例可透過擴充功能來尋找。

## <a name="sharing-results"></a>共用結果

<!-- TODO(Stefan): Need to fill in content/context for these bullets. If there's a lot of content, we might consider breaking this out into it's own doc. -->
如何在使用者/小組之間共用
* 檔目錄中的 Zip 專案
* 將專案複製到檔案共用
* 將小組共用提交的檔案位置新增至 Maquette 小組

<!-- TODO(Stefan): Need to break these out into their own sections and fill in the missing content/context. 
                   - Which of these is accessible now and not TBD?
-->
TBD
* 包含，以相對/絕對路徑、模組參考其他位置的程式碼
* 圖書館？
* 執行階段支援
* 未解析的外部-當專案遺失/損毀時的行為
* 我們可以新增/編輯/觀察與特定物件相關的腳本嗎？
  * 我們可以在其他地方複製/貼上此腳本嗎？
  * 物件屬性呢？
  * 在我的場景中命名物件？  (將腳本重新命名) 
  * 與物件相關聯之腳本的這個或本身關鍵字
  * 如果我在物件上按一下滑鼠右鍵，可以看到與它相關聯的程式碼 (與其所有階層) 
  * 我可以在 UI 中選取，並且在 VSCode 的程式碼中啟動嗎？
  * 在腳本來源檔案中將與物件相關聯的程式碼保持在一起？
  * 當我按一下物件時，將屬性視窗帶到該物件的上方？ 在 VR 和主要索引標籤中？
* 安全性問題
* 測試–可能是待定的，但我們可以建議以腳本的方式抓取影片或畫面格
* 如果我們有錯誤報表機制，我們可能會透過腳本讓他人存取 (？ ) .。。後
* 部署–如何「共用」結果，套件為 EXE
* 執行/控制示範或 spectating/監視
* 播放機模式
* 我們可能會有一段有關如何讓「元件」進行共用的區段？  (可能是 tbd) 
  * 有 #include 嗎？ 這會處理純 JS，但可能會有命名空間衝突。
  * 有什麼我們可以針對 maquette 合併其他具有命名物件的 maquette，以符合 JS 程式碼？
