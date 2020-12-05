---
title: Unreal 中的 UMG 和鍵盤
description: 瞭解如何使用 Unrealm 動畫圖形來建立小工具的 UI 系統。
author: hferrone
ms.author: suwu
ms.date: 11/25/2020
ms.topic: article
keywords: Windows Mixed Reality、全像移動、HoloLens 2、眼睛追蹤、眼睛輸入、前端掛載顯示器、Unreal 引擎、混合現實耳機、windows Mixed Reality 耳機、虛擬實境耳機、widget、UI、UMG、Unreal 運動圖形、Unreal 引擎、UE、UE4
ms.openlocfilehash: 59ad108a0e27298256f4f0d1661381a4f1748777
ms.sourcegitcommit: 32cb81eee976e73cd661c2b347691c37865a60bc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/04/2020
ms.locfileid: "96609759"
---
# <a name="umg-and-keyboard-in-unreal"></a>Unreal 中的 UMG 和鍵盤

Unreal 動畫圖形 (UMG) 是 Unreal 引擎的內建 UI 系統，用來建立功能表和文字方塊等介面。 使用 UMG 所建立的使用者介面是由小工具所組成。 我們將引導您建立新的 widget、將其新增至世界空間，以及使用系統鍵盤作為範例來啟用互動。 您可以在官方的 Unreal 引擎 [檔](https://docs.unrealengine.com/en-US/Engine/UMG/index.html)中深入瞭解 UMG。 

## <a name="create-a-new-widget"></a>建立新的小工具

- 建立 Widget 藍圖來配置遊戲的 UI：

![從 [Unreal] 功能表新增 widget 藍圖的螢幕擷取畫面](images/unreal-umg-img-01.png)

- 開啟新的藍圖，然後將元件從 [元件] 新增至畫布。  在此情況下，我們已從 [輸入] 區段新增兩個文字方塊元件：

![醒目提示和展開文字 widget 元件之階層視窗的螢幕擷取畫面](images/unreal-umg-img-02.png)

- 在 [階層] 或 [設計工具] 視窗中選取 widget，並修改 [詳細資料] 面板中的參數。  在此情況下，我們新增了一些預設的「提示文字」，以及當您將滑鼠停留在文字方塊上時所顯示的淡色色彩。  當您進行互動時，文字方塊將會顯示 HoloLens 上的虛擬鍵盤：

![階層視窗中已修改之參數的螢幕擷取畫面](images/unreal-umg-img-03.png)

- 您也可以在 [詳細資料] 面板中訂閱事件：

![詳細資料面板中事件的螢幕擷取畫面](images/unreal-umg-img-04.png)

## <a name="add-a-widget-to-world-space"></a>將 Widget 新增至世界空間

- 建立新的動作專案、新增 Widget 元件，並將動作專案加入場景中：

![已附加 widget 之執行者的螢幕擷取畫面](images/unreal-umg-img-05.png)

- 在 Widget 的詳細資料面板中，將 **Widget 類別** 設定為稍早建立的 widget 藍圖：

![具有 widget 類別集之 [藍圖詳細資料] 面板的螢幕擷取畫面](images/unreal-umg-img-06.png)

- 若為文字小工具，請確定未核取 [ **接收硬體輸入** ]，因此我們只會從虛擬鍵盤更新其文字：

![未核取 [接收硬體輸入] 的 [互動] 區段螢幕擷取畫面](images/unreal-umg-img-07.png)

## <a name="widget-interaction"></a>Widget 互動

UMG 小工具通常會從滑鼠接收輸入。  在 HoloLens 或 VR 上，我們需要模擬具有 Widget 互動元件的滑鼠，才能取得相同的事件。

- 建立新的動作專案、新增 **Widget 互動** 元件，並將動作專案加入場景中：

![反白顯示 widget 互動元件的新動作專案螢幕擷取畫面](images/unreal-umg-img-08.png)

- 在 Widget 互動元件的詳細資料面板中：
    - 將互動距離設定為您想要的距離值
    - 將 **互動來源** 設定為 **自訂**
    - 若為開發，請將 **Show Debug** 設為 **true**：

![Widget 互動和偵測元件屬性的螢幕擷取畫面](images/unreal-umg-img-09.png)

互動來源的預設值是 "World"，這應該會根據 Widget 互動元件的世界位置傳送 raycasts。 在 AR 和 VR 中，就不是這樣。  若要檢查 widget 互動元件是否符合您的預期，請務必啟用 [顯示偵錯工具] 並將暫留淡色新增至 widget。  因應措施是使用自訂來源，並從手光線的事件圖形中設定 raycast。  

在這裡，我們會從事件滴答進行呼叫：

![事件滴答的藍圖](images/unreal-umg-img-10.png)

然後，將虛擬滑鼠指標事件新增至 widget 互動元件，以回應 HoloLens 輸入。  在此情況下，當手 grasped 時，傳送左滑鼠按下事件，以及在未 grasped 的情況下，將滑鼠左鍵釋出事件：

![已新增虛擬滑鼠指標事件的藍圖](images/unreal-umg-img-13.png)

現在，當您將應用程式部署至 HoloLens 2 時，您會看到從右手邊延伸的手光線。 如果您將它導向其中一個可編輯的文字方塊和點擊，系統鍵盤將會出現在您面前，並可讓您輸入文字。 
 
> [!NOTE]
> HoloLens 系統鍵盤需要 Unreal Engine 4.26 或更新版本。 此外，只有當應用程式在裝置上執行時，才會在您的應用程式從 Unreal 編輯器串流到耳機時，不會出現鍵盤。

## <a name="see-also"></a>另請參閱：
* [Unreal 的 UMG 檔](https://docs.unrealengine.com/Engine/UMG/index.html)
* [Unreal 的 UMG 教學課程](https://docs.unrealengine.com/Programming/Tutorials/UMG/index.html)
