---
title: Advanced HoloLens Emulator 和混合現實模擬器
description: 使用鍵盤、滑鼠和 Xbox 控制器模擬 HoloLens Emulator 和 Windows Mixed Reality 模擬器輸入的詳細指示。
author: pbarnettms
ms.author: pbarnett
ms.date: 06/8/2020
ms.topic: article
keywords: HoloLens、Emulator、模擬、Windows Mixed Reality、混合現實耳機、Windows Mixed Reality 耳機、虛擬實境耳機
ms.openlocfilehash: a4e66b2738d5f89949b14fd6f901e2b30dc38cd9e02072f640345d374b9eb9fe
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2021
ms.locfileid: "115217124"
---
# <a name="advanced-hololens-emulator-and-mixed-reality-simulator-input"></a>進階 HoloLens 模擬器和混合實境模擬器輸入

大部分的模擬器使用者都只需要使用[HoloLens Emulator](using-the-hololens-emulator.md#basic-emulator-input)或[Windows Mixed Reality](using-the-windows-mixed-reality-simulator.md#basic-simulator-input)模擬器的基本輸入控制項。 下列詳細資料適用于已發現需要模擬更複雜類型之輸入的 advanced users。

## <a name="concepts"></a>概念

若要開始控制 HoloLens Emulator 和 Windows Mixed Reality 模擬器的虛擬輸入，您應該先瞭解一些概念。

動作是指控制和變更場景中某個事物的位置和方向。 針對目標可控制物件，動作會以旋轉和平移的方式來控制， (移動) 沿著三個軸。
* **偏擺**：向左或向右切換。
* **推銷**：開啟或關閉。
* 變換 **：端對端翻轉。**
* **X**：向左或向右移動。
* **Y**：向上或向下移動。
* **Z**：向前或向後移動。

筆勢和移動控制器輸入會緊密對應到實體裝置：
* **動作**：模擬按下食指至 thumb 的動作，或提取控制器上的 [動作] 按鈕。 例如，動作輸入可以用來模擬按下的動作、滾動內容，以及按下並按住。
* **[Bloom](../../design/system-gesture.md#bloom)/System 手勢或 Home**： HoloLens 的 Bloom/系統手勢或控制器的 [首頁] 按鈕，可用來返回 shell 並引發系統動作。

在 HoloLens 2 中，手上有豐富的標記法。  除了追蹤/未追蹤/可用於駕駛手勢之外，現在手中有一個可配合的基本架構模型，並對開發人員公開。  基本架構模型的每個手都有26個追蹤點。  
* **聯合**：在3d 空間中有關聯點的指定追蹤位置有20個追蹤的位置。
* **姿勢**：追蹤手中所有接點的完整集合，全部26個接點。 

我們目前不會透過模擬器公開個別聯合位置的直接控制，但您可以透過模擬 API 來設定它們。 我們有一組實用的代表性，可讓模擬器讓您切換。

您也可以控制模擬感應器輸入的狀態：
* **Reset**：將所有模擬的感應器傳回預設值。  從 HoloLens 2 Emulator 開始，重設的範圍可以是一或兩個手。 使用輔助按鍵 () 或按鈕 ()  (左和/或右邊的 Alt，或遊戲台) 上的左和/或右的 (，來與所需的) 互動。
* **追蹤**：迴圈流覽位置追蹤模式，包括：
  * **預設值**： OS 會根據系統發出的要求，選擇最佳的追蹤模式。
   * **方向**：無論系統要求，都會強制僅限方向的追蹤。
   * **位置**：無論系統要求為何，都會強制執行位置追蹤。

## <a name="types-of-input"></a>輸入類型

下表顯示每種類型的輸入如何對應至鍵盤、滑鼠和 Xbox 控制器。 每個類型都有不同的對應，視輸入控制模式而定。 您可以在本檔稍後的輸入控制模式找到詳細資訊。

| 輸入 |  鍵盤 |  滑鼠 |  Xbox 控制器 | 
|----------|----------|----------|----------|
|  Yaw |  向左/向右箭號 |  向左/向右拖曳 |  右邊的控制杆靠左/右 | 
|  音調 |  向上/向下箭號 |  向上/向下拖曳 |  右側的控制杆向上/向下 | 
|  Roll |  Q/E |  |  DPad 左/右 | 
|  X |  A/D |  |  左邊的操縱杆向左/向右 | 
|  Y |  Page up/page down |  |  向上/向下 DPad | 
|  Z |  W/S |  |  向左移/下移操縱杆 | 
|  動作 |  輸入或空格 |  向右按鈕 |  按鈕或觸發程式 | 
|  Bloom/系統 |  F2 或 Windows 鍵 |  |  B 按鍵 | 
|  控制器把手按鈕/手型抓住 |  G  |  |  | 
|  控制器功能表按鈕 |  M  |  |  | 
|  控制器觸控板觸控 |  U  |  |  | 
|  控制器按觸控板 |  P  |  |  | 
|  控制器操縱杆按鍵 |  K  |  |  | 
|  左方控制器追蹤狀態 |  F9 |  |  | 
|  右控制器追蹤狀態 |  F10 |  |  | 
|  手上「Close」姿勢 | 7 |  |  |
|  將「開啟」姿勢 (預設)  | 8 |  |  |
|  手上點姿勢 | 9 |  |  |
|  手上「縮小」姿勢 | 0 |  |  |
|  重設 |  Escape 鍵 |  |  [開始] 按鈕 | 
|  追蹤 |  T 或 F3 |  |  X 按鈕 | 


注意：控制器按鈕可以設定為一個手形/控制器，或使用手動目標修飾詞來設定。

## <a name="targeting"></a>目標 

上述的一些輸入概念會各自獨立。  Action、Bloom/System、Reset 和追蹤是完整的概念、不需要，而且不受任何目標的其他修飾詞所影響。  其餘的概念可以套用至多個目標的其中一個。 我們引進了一些方法，讓您指定要套用命令的目標目標。  在所有情況下，都可以透過 UI 或透過鍵盤按下（要設為目標的物件）來指定。  在某些情況下，您也可以直接使用 xbox 控制器來指定。 

下表說明目標的選項，以及啟用這些選項的方式。

| Object | 鍵盤修飾詞 | 控制器修飾詞 | EmulatorUI 修飾詞 |
|----------|----------|----------|----------|
| 主體 | (預設值) | (預設值) | (預設值) |
| Head | 按住 H | (無法使用) | (無法使用) |
| 左側/控制器 | 按住左 Alt 按鈕 | 保留有肩的按鈕 | Left-Hand 圖釘 | 
| 右手/控制器 | 按住右鍵 Alt 按鈕 | 保存適當的肩按鈕 | Right-Hand 圖釘 |
| 眼睛 | 保留 Y | (無法使用) | 眼睛圖釘 |
  
下表顯示每個目標修飾詞如何對應每個核心移動輸入概念

| 輸入 | 預設 (主體)  |  手/控制器 (按住 Alt、按住遊戲台肩按鈕或切換 UI 圖釘)  |  Head (保存 H)   |  眼睛 (按住 Y 或切換 UI 圖釘)  |
|----------|----------|----------|----------|----------|
|  Yaw |  將主體左移/右移 |  左移/右移 |  將標頭左移/右移 | 眼睛看起來靠左/右 |
|  音調 |  開啟/下移 |  前移/下移 |  開啟/下移 | 眼睛眼睛查閱/下移 | 
|  Roll |  向前或向右滾動 |  |  向前或向右滾動 |  (沒有任何動作)  |
|  X |  向左/向右投影片 |  左右移動手形/控制器 |  將標頭左移/右移 |  (沒有任何動作)  |
|  Y |  將主體向上/向下移動 |  向上/向下移動手形/控制器 |  開啟/下移 |  (沒有任何動作)  |
|  Z |  將主體向前/向後移動 |  向前/向後移動手形/控制器 |  開啟/下移 |  (沒有任何動作)  |
 
 
## <a name="controlling-an-app"></a>控制應用程式

以下是建議的每日使用控制項集合：

|  作業 |  鍵盤和滑鼠 |  控制器 | 
|----------|----------|----------|
|  主體 X |  A/D |  左邊的操縱杆向左/向右 | 
|  主體 Y |  Page up/page down |  向上/向下 DPad | 
|  主體 Z |  W/S |  向左移/下移操縱杆 | 
|  主體偏擺 |  向左/向右鍵拖曳滑鼠 |  右邊的控制杆靠左/右 | 
|  Head 偏擺 |  H + 向左/向右拖曳滑鼠 |  H (鍵盤上的) + 右邊的控制杆左邊/右邊 | 
|  頭部推銷 |  向上/向下拖曳滑鼠 |  右側的控制杆向上/向下 | 
|  頭部滾動 |  Q/E |  DPad 左/右 | 
|  手形/控制器 X |  Alt + A/D |  肩 + 左方操縱杆左/右 | 
|  手形/控制器 Y |  Alt + Page up/page down |  肩 + DPad 向上/向下 | 
|  手形/控制器 Z |  Alt + W/S |  肩 + 左方操縱杆向上/向下 | 
|  手形/控制器偏擺 |  Alt + 向左/向右拖曳滑鼠 |  肩 + 右邊的控制杆左/右 | 
|  手/控制器的音調 |  Alt + 向上/向下拖曳滑鼠 |  肩 + 右邊的控制杆向上/向下 | 
|  手形/控制器滾動 |  Alt + Q/E |  肩 + DPad 左/右 | 
|  動作 |  滑鼠右鍵 |  觸發程序 | 
|  Bloom/系統/首頁 |  F2 或 Windows 鍵 |  B 按鍵 | 
|  重設 |  逸出 |  [開始] 按鈕 | 
|  追蹤 |  T |  X 按鈕 | 
|  捲動 |  Alt + 滑鼠右鍵鍵 + 向上/向下拖曳滑鼠 |  肩 + 觸發程式 + 右邊的控制杆向上/向下 | 
|  移動/旋轉更快 | 向左或向右 Shift 鍵 | 按住適當的操縱杆 |
|  移動/旋轉慢 | 向左或向右 Ctrl 鍵 | 按住左邊的操縱杆 |

## <a name="using-a-windows-mixed-reality-immersive-headset-and-motion-controllers-with-the-hololens-2-emulator"></a>搭配使用 Windows Mixed Reality 沉浸式頭戴裝置和運動控制器與 HoloLens 2 模擬器

使用 Windows Mixed Reality 具有 HoloLens 2 Emulator 的沉浸式耳機時，移動和旋轉會自動對應到耳機移動和旋轉。  移動控制器的位置和方向會自動對應至模擬器中的手邊位置和方向。  下表列出使用移動控制器時可使用的其他動作。

> [!NOTE]
> 使用耳機時，系統會自動忽略標準鍵盤、滑鼠和遊戲台控制項。

|  作業 |  動作 |  備註 | 
|----------|----------|----------|
|  主體 X |  向左/向右操縱杆 |   | 
|  主體 Z |  向前/向後的操縱杆 |   | 
|  主體 Y |  鍵盤頁面向上/Down | 確定 Windows Mixed Reality 具有焦點。  如果焦點是在 Windows Desktop 上時，請按 Win + Y，以將焦點歸還至 Windows Mixed Reality。 |
|  向左或向右尋找眼睛 |  DPad 左/右 | |
|  眼睛查閱/下移 | 向上/向下 DPad | |
|  點選 | 觸發程序 | |
|  縮小/理解 | 底框按鈕 | |
|  系統手勢 | 功能表按鈕 | |
|  重設位置 | 操縱杆按一下 | |

## <a name="perception-simulation-control-panel-keyboard-shortcuts"></a>感知模擬主控台鍵盤快速鍵

您可以使用下列鍵盤快速鍵來存取 [感知模擬] 控制台，並啟用或停用電腦輸入裝置。

| 作業 | 快速鍵 | 描述/附注 |
|-----------|----------|-------------|
| 切換 [使用鍵盤進行模擬] | F4 | 當關閉時，鍵盤輸入會移至 HoloLens 或 Windows Mixed Reality 應用程式。 |
| 切換「使用滑鼠進行模擬」 | F5 | 當關閉時，會將滑鼠輸入移至 Mixed Reality 環境 (只 Windows Mixed Reality)  |
| 切換「使用遊戲台進行模擬」 | F6 | 當關閉時，模擬會忽略遊戲者輸入 |
| 顯示或隱藏控制台 | F7 | |
| 將鍵盤焦點設定在控制台中 | F8 | 如果目前看不到該面板，則會先顯示。 |
| 在模擬器或混合實境入口視窗中停駐或取消停駐面板 | F9 | 如果視窗在未停駐時關閉，則會停駐並隱藏。 |

## <a name="see-also"></a>另請參閱
* [安裝工具](../install-the-tools.md)
* [使用 HoloLens 模擬器](using-the-hololens-emulator.md)
* [使用 Windows Mixed Reality 模擬器](using-the-windows-mixed-reality-simulator.md)
