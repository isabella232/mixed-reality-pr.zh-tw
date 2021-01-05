---
title: 手勢指導
description: 當系統未偵測到使用者的手協助時，所觸發的3D 手。
author: grayclee
ms.author: glee
ms.date: 09/25/2019
ms.topic: article
keywords: Windows Mixed Reality、設計、手輔導、沉浸式耳機、MRTK、手、協助手、混合現實耳機、windows Mixed reality 耳機、虛擬實境耳機、HoloLens、MRTK、混合現實工具組
ms.openlocfilehash: e46704a1cd2e93fc1764528c408c01d117444c34
ms.sourcegitcommit: d340303cda71c31e6c3320231473d623c0930d33
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/01/2021
ms.locfileid: "97847965"
---
# <a name="hand-coach"></a>手勢指導

![範例：手形指導](images/HandCoach/MRTK_handCoach.jpg)<br>

當系統未偵測到使用者的手時，手上的教練會觸發3D 模型化的手。 這項功能是一個「教學」元件，可在未教授手勢時協助引導使用者。 如果使用者尚未針對某個句號完成指定的手勢，則手會有延遲的迴圈。 手形指導可用來代表按下按鈕或挑選全像影像。  

## <a name="hand-coach-provided"></a>提供的手勢

目前的互動模型代表各式各樣的手勢控制項，例如滾動、遠選和近端點擊。 以下是<a href="https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets"> MRTK</a>中所提供之現有手勢的完整清單：

:::row:::
    :::column:::
       ![接近 Select 的範例](images/HandCoach/NearSelect.gif)<br>
       **接近選擇使用的範例顯示如何選取按鈕或關閉互動物件**<br>
    :::column-end:::
    :::column:::
       ![點擊點範例](images/HandCoach/AirTap.gif)<br>
        **用來顯示如何選取遠距離的物件的點擊範例**<br>
    :::column-end:::
    :::column:::
       ![移動的範例](images/HandCoach/Move.gif)<br>
       **移動空間中物件的範例，用來示範如何在空間中移動全息圖**<br>
    :::column-end:::
    :::column:::
       ![旋轉範例](images/HandCoach/Rotate.gif)<br>
       **示範如何旋轉全像全像是影像或物件的 Rotate-Used 範例**<br>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       ![調整規模範例](images/HandCoach/Scale.gif)<br>
       **相應縮小範例，用來示範如何操作大容量**<br>
    :::column-end:::
    :::column:::
       ![手掌的範例](images/HandCoach/PalmUp.gif)<br>
        **用來顯示快顯功能表的上方範例-建議使用**<br>
    :::column-end:::
    :::column:::
       ![HandFlip 範例](images/HandCoach/HandFlip.gif)<br>
       **手勢範例-另一種顯示功能表的方法**<br>
    :::column-end:::
    :::column:::
       ![滾動的範例](images/HandCoach/Scoll.gif)<br>
       **滾動範例-用於滾動清單或長檔**<br>
    :::column-end:::
:::row-end:::

## <a name="design-concepts"></a>設計概念

針對 Hololens2，我們根據 instinctual 和自然手勢來設計出互動。 我們相信大部分的使用者都可以直覺化，因此我們不會建立專用的手勢學習時間。 相反地，我們建立了一項指導，以協助使用者瞭解這些手勢是否停滯，或不熟悉全像全息圖互動。 在沒有學習的時候，我們認為顯示使用者如何藉由示範來執行動作，這是最佳選項。 我們發現使用者能夠找出手勢，但需要一些指引。 如果我們偵測到使用者未與某個物件進行互動，則會觸發適當的手勢和手指放置。 

### <a name="intuitive"></a>直觀

製作手動畫時，應該很明顯，不會造成任何混淆。 手動畫是您嘗試提示使用者瞭解的手勢標記法。 

例如，如果您希望使用者按下按鈕，就會觸發按下按鈕的動作。

![範例：近乎點擊的手勢](images/HandCoach/NearSelect_unity.gif)<br>
*示範近乎點擊 Gem 的手勢*  

### <a name="hand-scale"></a>手擴展

我們使用 UI 功能表來測試各種手上的大小，並覺得如果手上的大小為真，則會提供阻感受。 如果太小，就很難查看並瞭解手勢。 

**語氣和手**

不要預期使用者可透過語音聆聽一組指示，並透過手動指導來觀看不同的指示。 排序您的指示，以協助使用者專注于競爭，以減少感應式多載。


## <a name="can-i-create-my-own"></a>我可以建立自己的嗎？

可以！ 建議您為您的遊戲建立自己的獨特手勢，並貢獻回該社區！
我們提供 Rigged 手的 Maya 檔，可用於您的應用程式，您可以在這裡下載： <a href="files/HandCoach_MRTK.zip"> 下載 HandCoach_MRTK.zip </a>

![Maya 中的動畫指標範例](images/HandCoach/MayaSelect_Gif.gif)<br>
*在 Maya 中刺探方塊的動畫手勢範例*


**建議的 authoring tool**

在3D 演出者之間，許多選擇使用 [Autodesk 的 Maya，可以使用 HoloLens](https://www.youtube.com/watch?v=q0K3n0Gf8mA) 來轉換資產的建立方式。 提供的手入檔案是 Maya 二進位檔案，因此建議使用 Maya 來建立動畫和匯出手。 如果您想要使用其他3D 程式，以下是 <b>。FBX</b>： <a href="files/HandCoachMRTK_FBX.zip"> 下載 HandCoachMRTK_FBX.zip </a> 以建立您自己的控制器設定。 

如果使用提供的可下載 maya 檔，建議您將 unity 中的手縮小為0.6。

![範例： Maya 中的手教練裝備](images/HandCoach/MayaExample.png)<br>
*Rigged 手*

### <a name="technical-specs"></a>技術規格

*   Maya Ascii 格式有兩個右手檔案可用
*    右邊和左方都提供 Maya 二進位格式
*   將 Maya 檔案設定為 24 FPS
*   在檔案中，有左方和右手邊，可用於兩個右手或單次手勢。 預設只會顯示右手邊。
*   建議將大約10個框架的緩衝區留在開頭和結尾，以淡化
*   如果使用指定的目標建立物件的動畫，它的最佳作法是建立預設方塊或 Null 的動畫。
*   如果手上有一個實體物件（例如方塊）的動畫，它的最佳作法是不要在 Maya 中製作轉譯的動畫，但等候在 Unity 或程式碼中建立動畫。
*   可見的動畫應為1.5 秒，才能傳達有意義的資訊
*   當您感到滿意動畫時：
    *   選取所有接點並製作主要畫面格
    *   刪除控制器，選取接點和網狀，然後匯出為 FBX
    *  如果有多個動畫，您可以使用 Maya 的內建遊戲匯出工具： https://knowledge.autodesk.com/support/maya/learn-explore/caas/CloudHelp/cloudhelp/2015/ENU/Maya/files/Game-Exporter-htm.html

## <a name="exporting-from-maya"></a>從 Maya 匯出

當您滿意動畫之後
* 選取所有接點：選取 > 階層

     ![範例：功能表中的階層](images/HandCoach/Hierarchy.png)<br>
* 製作您的動畫：切換至動畫 > 按鍵 > 製作動畫

     ![範例：製作動畫功能表位置](images/HandCoach/BakeAnimation.png)<br>
* 刪除控制器 Rig： Outliner > MainR_Grp 或 MainL_Grp

     ![範例：控制器 Rig 功能表位置](images/HandCoach/ControllerRig.png)<br>

* 匯出為 FBX：選取 .JNT + 網格：檔案 > 匯出選取範圍 (選項方塊) > 匯出選取專案

     ![範例：匯出選取專案功能表位置](images/HandCoach/OptionBox.png)<br>

     ![範例：功能表位置](images/HandCoach/SelectionExport.png)<br>

     ![範例：匯出選項功能表位置](images/HandCoach/FBXSelection.png)<br>


 當匯出為 FBX 並帶入 Unity 時，請將手向下調整為0.6。 我們發現這是實際顯示的完美平衡。 

![範例： Unity 設定](images/HandCoach/HandHintScale.png)<br>
*在 MRTK 中找到 HandCoach_R 預製專案的 Unity 設定*


## <a name="implementing-hands-into-your-unity-project"></a>實際執行您的 Unity 專案

### <a name="best-practices"></a>最佳作法

* 建議您將 unity 中的手縮小至0。6
* 雙手應該播放兩次，如果未完成，則會持續迴圈直到手勢完成為止。 雙手應迴圈兩次，以確保使用者有時間註冊並查看手勢。 手應該在迴圈之間淡入和縮小。 
 *  如果 HL2 攝影機看到使用者的手，但使用者未進行需要的互動，則手會在10秒後出現。
*   如果 HL2 攝影機看不到使用者的手，就會在5秒後出現手。  
*   如果在動畫中間的 HL2 攝影機會以明顯的方式追蹤使用者的手，動畫將會完成並淡出。
*   如果您要包含語音，建議您將其對應至手的手勢。
*   如果您至少教授過一次，只要偵測到使用者停滯，請只重複手勢。
*   如果特定的手指/手位置很重要，請確保使用者可以清楚地在動畫中看到這些細微差異。 試著 angling 手，讓最重要的部分清楚可見。 
* 如果您注意到手上的失真，您需要移至 Unity 的品質設定來提高骨骼數目。 
 移至 Unity 的 [編輯] > 專案設定 > 品質 > 其他 > Blend 加權。 確定已選取「4個骨骼」以查看平滑接點。 

   ![範例：專案設定視窗](images/HandCoach/ProjectSettings.png)<br>


### <a name="what-to-avoid"></a>避免事項

* 調整手太大
* 把手放在使用者附近
* 手中應只教授一次。 透過教學可能會造成混淆和 messiness
*   將它帶入 Unity，請在這裡下載最新的 MRTK： https://github.com/microsoft/MixedRealityToolkit-Unity
    *   材質： Teaching_Hand2
    *   腳本：請參閱 MRTK 指導方針以取得<a href= "https://github.com/MixedRealityToolkit-Unity/blob/'HandCoachUX'/Documentation/README_HandCoach.md">MRTK</a>的指導方針
    *   每個專案的設定
        *   設定為 UWP 的場景：您可以在設定 [Unity 專案](../develop/unity/Configure-Unity-Project.md) 中找到 Windows Mixed Reality 的指示。

## <a name="see-also"></a>請參閱

* [互動-基礎](interaction-fundamentals.md)
* [資產建立流程](asset-creation-process.md)
* [軌跡](../gestures.md)
* [安裝工具](../develop/install-the-tools.md)
* [設定 Unity 專案](../develop/unity/Configure-Unity-Project.md)
* [Unity 開發概觀](../develop/unity/unity-development-overview.md)
* [MRTK 101](../develop/unity/mrtk-101.md)
