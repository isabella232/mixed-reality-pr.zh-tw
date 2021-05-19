---
title: 目視追蹤範例總覽
description: 在 MRTK 中建立 eyetracking 的範例
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、EyeTracking、
ms.openlocfilehash: b5fd3ee35e54c54f2f6b21dc1ce53625c68f65b4
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144680"
---
# <a name="eye-tracking-examples"></a>目視追蹤範例

本主題說明如何在 MRTK 中建立 MRTK 眼睛追蹤範例（ (資產/MRTK/範例/示範/EyeTracking) ），以快速開始使用眼睛追蹤。
這些範例可讓您體驗其中一個新的神奇輸入功能： **眼睛追蹤**！
此示範包含各種使用案例，範圍從隱含的眼睛型啟用到如何順暢地結合您正在尋找的資訊與 **語音** 和 **手寫** 輸入相關資訊。
如此一來，使用者就可以透過查看目標並說出「 _選取_ 」或執行手勢，快速且輕鬆地在其觀點中選取和移動全像攝影內容。
示範中也包含了眼睛導向滾動、文字的平移和縮放，以及平板的影像。
最後，會提供一個範例來錄製和視覺化使用者對2D 平板的視覺效果。
在下一節中，您將會在 MRTK 眼睛追蹤範例套件 (資產/MRTK/範例/示範/EyeTracking) 包含的每個不同範例中，找到更多詳細資料：

![眼睛追蹤場景清單](../images/eye-tracking/mrtk_et_list_et_scenes.jpg)

下一節簡要說明個別的眼睛追蹤示範場景。
MRTK 眼追蹤示範場景已 [載入額外](https://docs.unity3d.com/ScriptReference/SceneManagement.LoadSceneMode.Additive.html)，我們將在下面說明如何進行設定。

## <a name="overview-of-the-eye-tracking-demo-samples"></a>目視追蹤示範範例簡介

### <a name="eye-supported-target-selection"></a>[**目視支援的目標選取範圍**](../input/eye-tracking/eye-tracking-target-selection.md)

本教學課程示範如何輕鬆地存取眼睛資料來選取目標。
其中包含微妙但功能強大的意見反應範例，可讓使用者確信目標的焦點不會變大。
此外，也有一個簡單的智慧型通知範例，會在讀取後自動消失。

**摘要**：使用眼睛、語音和手寫輸入的組合，快速且輕鬆地選取目標。

### <a name="eye-supported-navigation"></a>[**目視支援的導覽**](../input/eye-tracking/eye-tracking-navigation.md)

假設您正在閱讀有關遠處顯示器或電子讀者的一些資訊，當您到達顯示文字的結尾時，文字會自動向上滾動以顯示更多內容。
或者，如何以神奇的方式直接縮放至您所看到的位置？
以下是本教學課程中展示有關眼睛支援導覽的一些範例。
此外，也有一個範例，可讓您根據目前的焦點自動旋轉，來旋轉3D 全像投影。

**摘要**：使用眼睛、語音和手寫輸入的組合來移動捲軸、平移、縮放、3d 旋轉。

### <a name="eye-supported-positioning"></a>[**目視支援的定位**](../input/eye-tracking/eye-tracking-eyes-and-hands.md)

本教學課程會顯示稱為 [Put-的](https://youtu.be/CbIn8p4_4CQ) 輸入案例，也就是在早期的1980和語音輸入中，從 MIT 媒體實驗室的可追溯回到研究。
這是很簡單的概念：從您的眼睛中獲益，以提供快速目標選擇和定位。
只要看一下一個全息圖，然後說 [ _put this （放置這_ 一點）]，再看一下您要放置它的位置，然後說「 _有！_」。
若要更精確地放置全息圖，您可以使用來自您手、語音或控制器的其他輸入。

**摘要**：使用眼睛、語音和手輸入來定位全息 (*拖放*) 。 使用眼睛 + 手的眼睛支援滑杆。

### <a name="visualization-of-visual-attention"></a>**視覺效果的視覺效果**

以使用者外觀為基礎的資料，可讓您以極強大的工具來評估設計的可用性，並在有效率的工作資料流程中找出問題。
本教學課程會討論不同的眼睛追蹤視覺效果，以及它們如何符合不同的需求。
我們提供記錄和載入眼睛追蹤資料的基本範例，以及如何將其視覺化的範例。

**摘要**：在平板上 (熱度圖) 的二維強調地圖。 錄製 & 重新執行眼睛追蹤資料。

## <a name="setting-up-the-mrtk-eye-tracking-samples"></a>設定 MRTK 眼追蹤範例

### <a name="prerequisites"></a>必要條件

請注意，在裝置上使用眼睛追蹤範例需要 HoloLens 2，以及使用套件 Package.appxmanifest 上的「注視輸入」功能建立的範例應用程式套件。

為了在裝置上使用這些眼睛追蹤範例，請務必遵循 [這些步驟](../input/eye-tracking/eye-tracking-basic-setup.md#testing-your-unity-app-on-a-hololens-2) ，然後再 Visual Studio 中建立應用程式。

### <a name="1-load-eyetrackingdemo-00-rootsceneunity"></a>1. Load EyeTrackingDemo-00-RootScene unity

*EyeTrackingDemo-00-RootScene* 是基底 (_根_) 場景，其中包含所有核心 MRTK 元件。
這是您必須先載入的場景，您將在其中執行眼睛追蹤示範。
它有一個圖形化的場景功能表，可讓您輕鬆地在將 [載入額外](https://docs.unity3d.com/ScriptReference/SceneManagement.LoadSceneMode.Additive.html)的不同眼睛追蹤範例之間切換。

![目視追蹤範例中的場景功能表](../images/eye-tracking/mrtk_et_scenemenu.jpg)

根場景包含一些核心元件，這些元件會跨額外載入的場景保存，例如 MRTK 設定的設定檔和場景相機。
_MixedRealityBasicSceneSetup_ (請參閱下面的螢幕擷取畫面) 包含會在啟動時自動載入參考場景的腳本。
根據預設，這是 _EyeTrackingDemo-02-TargetSelection_。  

![OnLoadStartScene 腳本的範例](../images/eye-tracking/mrtk_et_onloadstartscene.jpg)

### <a name="2-adding-scenes-to-the-build-menu"></a>2. 將場景新增至 [組建] 功能表

若要在執行時間載入加法場景，您必須先在組建功能表中將這些場景新增至 _組建設定-> 場景_ 。
將根場景顯示為清單中的第一個場景是很重要的：

![目視追蹤範例的組建設定場景功能表](../images/eye-tracking/mrtk_et_build_settings.jpg)

### <a name="3-play-the-eye-tracking-samples-in-the-unity-editor"></a>3. 在 Unity 編輯器中播放眼睛追蹤範例

將眼睛追蹤場景新增至組建設定並載入 _EyeTrackingDemo-00-RootScene_ 之後，您可能會想要檢查的最後一件事：是否已啟用附加至 _MixedRealityBasicSceneSetup_ GameObject 的 _' OnLoadStartScene '_ 腳本？ 這是為了讓根場景知道要先載入的示範場景。

![OnLoad_StartScene 腳本的範例](../images/eye-tracking/mrtk_et_onloadstartscene.jpg)

現在就開始吧！ 點擊「 _Play_」！
您應該會看到數個 gem，以及頂端的場景功能表。

![ET 目標選取場景的範例螢幕擷取畫面](../images/eye-tracking/mrtk_et_targetselect.png)

您也應該會在遊戲視圖的中央看到一個小型半透明圓圈。
這可做為 _模擬眼睛_ (游標) 的指標：只要按下滑鼠 _右鍵_ 並移動滑鼠，即可變更其位置。
當游標停留在 gem 上方時，您會發現它會貼齊到目前所觀看 gem 的中央。
這是一個很好的方法，可以測試在目標上「 _尋找_ 」事件是否如預期般觸發。
請注意，透過滑鼠控制的 _模擬眼睛_ 是對我們的快速和意外眼睛的補充，相當不良。
不過，它很適合用來測試基本功能，然後再將其部署到 HoloLens 2 裝置上，然後再逐一查看設計。
回到我們的眼睛追蹤範例場景： gem 會旋轉一段時間，只要經過查看，並可在其上「查看」和 .。。

- 按 _enter_ (模擬說「select」 ) 
- 說「 _選取_ 」您的麥克風
- 當按下 _空格鍵_ 顯示模擬的手輸入時，請按一下滑鼠左鍵來執行模擬的縮小

我們會更詳細地說明如何在 [**支援的目標選擇**](../input/eye-tracking/eye-tracking-target-selection.md) 教學課程中達成這些互動。

將游標移到場景的頂端功能表列時，您會發現目前的動態顯示專案會稍微反白顯示。
您可以使用上述其中一個描述的 commit 方法來選取目前反白顯示的專案 (例如，按 _enter_) 。
如此一來，您就可以在不同的眼睛追蹤範例場景之間切換。

### <a name="4-how-to-test-specific-sub-scenes"></a>4. 如何測試特定的 sub 場景

在特定案例中，您可能不會想要每次都經過場景功能表。
相反地，您可能會想要在按下 [ _播放_ ] 按鈕時，直接從您目前正在處理的場景中開始。
沒問題！ 以下是您可以執行的動作：

1. 載入 _根_ 場景
2. 在 _根_ 場景中，停用 _' OnLoadStartScene '_ 腳本
3. 將下列 (或任何其他場景) 所述的眼睛追蹤測試場景 _拖放_ 到 _階層視圖中_，如下列螢幕擷取畫面所示。

    ![加法場景範例](../images/eye-tracking/mrtk_et_additivescene.jpg)

4. 按下 _播放_

請注意，載入這類的子場景並非持續性：這表示如果您將應用程式部署至 HoloLens 2 裝置，則只會載入根場景， (假設它出現在您的組建設定) 的上方。
此外，當您與其他人共用您的專案時，不會自動載入子場景。

---

現在您已經知道如何讓 MRTK 眼追蹤範例幕後運作，接下來讓我們繼續深入探討如何使用眼睛來選取全像投影： [支援的目標選擇](../input/eye-tracking/eye-tracking-target-selection.md)。

---
[回到「MixedRealityToolkit 中的眼睛追蹤」](../input/eye-tracking/eye-tracking-Main.md)
