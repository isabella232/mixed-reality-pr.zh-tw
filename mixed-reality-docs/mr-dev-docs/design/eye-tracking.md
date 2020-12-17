---
title: 眼球追蹤
description: HoloLens 2 讓開發人員能夠使用使用者所查看的資訊，讓開發人員能夠使用新的內容層級，並在全像人類的經驗中理解。
author: sostel
ms.author: sostel
ms.date: 10/29/2019
ms.topic: article
keywords: 眼睛追蹤、混合現實、輸入、眼睛、校正、混合現實耳機、windows mixed reality 耳機、虛擬實境耳機、HoloLens、MRTK、混合現實工具組、意圖、動作
ms.openlocfilehash: 53a44fab72d3a15df3cf5929c6ddda4fec06af71
ms.sourcegitcommit: 2bf79eef6a9b845494484f458443ef4f89d7efc0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/17/2020
ms.locfileid: "97612862"
---
# <a name="eye-tracking-on-hololens-2"></a>HoloLens 2 的眼球追蹤

![MRTK 中的眼睛追蹤示範](images/mrtk_et_scenemenu.jpg)

HoloLens 2 讓開發人員能夠使用使用者所查看的資訊，讓開發人員能夠使用新的內容層級，並在全像人類的經驗中理解。 本頁面說明開發人員如何從各種使用案例的眼睛追蹤中獲益，以及設計眼睛型使用者互動時要尋找的內容。 

眼睛追蹤 API 已設計為使用者的隱私權，避免傳遞任何可識別的資訊，特別是任何生物特徵辨識。 針對感知感知的應用程式，使用者必須授與應用程式許可權以使用眼睛追蹤資訊。 


### <a name="device-support"></a>裝置支援
<table>
<colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
</colgroup>
<tr>
     <td><strong>功能</strong></td>
     <td><a href="../hololens-hardware-details.md"><strong>HoloLens (第 1 代)</strong></a></td>
     <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
     <td><a href="../discover/immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></td>
</tr>
<tr>
     <td>眼睛</td>
     <td>❌</td>
     <td>✔️</td>
     <td>❌</td>
</tr>
</table>

<br>

## <a name="calibration"></a>校正 
為了讓眼睛追蹤能準確地運作，每位使用者都必須經過 [眼睛追蹤使用者校正](../calibration.md) ，讓使用者能夠查看一組全像全像一組的目標。 這可讓裝置為使用者調整系統，以獲得更舒適且更高品質的觀賞體驗，並同時確保一致的眼睛追蹤。 

目視追蹤應該適用于大部分的使用者，但在少數情況下，使用者可能無法成功校正。 校正可能會因各種原因而失敗，包括但不限於： 
* 使用者先前退出宣告校正流程
* 使用者有注意力，未遵循校正目標
* 使用者有特定類型的 contact 鏡頭以及系統尚不支援的眼鏡 
* 使用者有特定的眼睛生理學、眼睛狀況或具有系統尚未支援的目視外科  
* 外部因素抑制可靠的眼睛追蹤，例如 HoloLens 面板上的塗抹或眼鏡、密集的直接陽光和遮蔽，因為眼睛正面的頭髮

開發人員應務必為使用者提供適當的支援，以找出可能無法 (的眼睛追蹤資料) 。 我們已在此頁面底部的區段中，提供回復解決方案的建議。 

若要深入瞭解校正，以及如何確保順暢的體驗，請查看我們的 [眼睛追蹤使用者校正](../calibration.md) 頁面。

<br>

## <a name="available-eye-tracking-data"></a>可用的眼睛追蹤資料
在深入探討眼睛輸入的特定使用案例之前，我們想要簡短指出 HoloLens 2 的 [眼睛追蹤 API](https://docs.microsoft.com/uwp/api/windows.perception.people.eyespose) 所提供的功能。 開發人員可存取單一眼睛的光線 (注視的原點和方向) 大約 _30 FPS (30 Hz)_。
如需有關如何存取眼睛追蹤資料的詳細資訊，請參閱我們的開發人員指南，以瞭解如何在您的 [DirectX](../develop/native/gaze-in-directx.md) 和 [Unity 中](https://aka.ms/mrtk-eyes)使用眼睛。

預測的眼睛大約是在實際目標 (的視覺角度1.5 度以內，請參閱下圖) 。 由於預期會有些許的 imprecisions，因此開發人員應該規劃這項下限值周圍的一些邊界 (例如，2.0-3.0 度可能會導致) 更熟悉的體驗。 我們將在下方討論如何處理小型目標的選取。 為了讓眼球追蹤精準運作，每個使用者都必須接受眼球追蹤使用者校正。 

![距離 2 公尺的最佳目標大小](images/gazetargeting-size-1000px.jpg)<br>
*雙計量距離的最佳目標大小*

<br>

## <a name="use-cases"></a>使用案例
眼球追蹤可讓應用程式即時追蹤使用者的視線方向。 下列使用案例說明在混合現實 HoloLens 2 上進行眼追蹤時可能發生的一些互動。
請注意，這些使用案例還不是「全像全像」 Shell 體驗的一部分， (也就是當您啟動 HoloLens 2) 時所看到的介面。
您可以在「 [混合現實」工具](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Main.html)組中試用其中一部分，這會提供數個有趣且功能強大的範例來使用眼睛追蹤，例如快速且輕鬆地查看支援的目標選項，以及根據使用者查看的內容自動滾動文字。 

### <a name="user-intent"></a>使用者意圖    
使用者查看位置和內容的相關資訊，可 **為其他輸入** 提供功能強大的內容，例如語音、手和控制器。
這可以運用在各種不同的工作上。
例如，這可以從快速且輕鬆地以場景為 **目標**，只要查看一組影像，然後說「選取」 (也會 [看到「](gaze-and-commit.md) *選取*」也看到) 或「 *put this ...*」，然後查看使用者想要放置全像 *有*。 您可以在[混合實境工具組 - 視線導向目標選取](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_TargetSelection.html)和[混合實境工具組 - 視線導向目標定位](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Positioning.html)中找到相關範例。

此外，使用者意圖的範例可能包括使用使用者查看的相關資訊，以增強與各有虛擬專員和互動式全息的互動。 例如，虛擬專員可能會根據目前已查看的內容，來調整可用的選項和其行為。 

### <a name="implicit-actions"></a>隱含動作
隱含動作的類別與使用者意圖有密切的關係。
它的概念是，全像是全像是 instinctual 的影像或使用者介面專案，可能不會覺得使用者完全與系統互動，而是由系統和使用者保持同步。其中一個範例是以 **眼睛為基礎的自動滾動** ，其中使用者可以讀取長文字，此文字會在使用者到達文字方塊的底部時自動開始滾動，而不需要抬起手指。  
其中一個重要層面是，捲動速度會調整為使用者的閱讀速度。
另一個範例是 **眼睛支援的縮放和平移** ，讓使用者可以覺得完全朝著他的焦點。 觸發和控制縮放速度可透過聲音或手寫輸入來控制，這對於提供使用者感覺來掌控控制項，同時避免發生大量的情況相當重要。 我們將在下面更詳細討論這些設計考慮。 一旦放大之後，使用者就可以順暢地遵循，例如，街道的某一堂，只要使用他們的眼睛，就可以探索他或她的鄰近地區。
您可以在[混合實境工具組 - 視線導向瀏覽](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Navigation.html)範例中找到這類互動的示範。

_隱含動作_ 的其他使用案例可能包括：
- **智慧型通知：** 在您想要的位置上快顯通知的感到苦惱？ 考慮到使用者所注意的內容，您可以藉由從使用者目前撥雲見日的位置來抵銷通知，讓這項體驗更好。 這會限制分散注意力，並在使用者完成閱讀之後自動將其關閉。 
- **用心全像影像：** Gazed 時，會稍微反應的全像投影。 這可以從稍微照亮的 UI 元素範圍內，以緩慢的綻放花卉為虛擬狗，從使用者回頭看看，並 wagging 它的結尾。 這項互動可能會在您的應用程式中提供連線能力和滿意度的有趣意義。

### <a name="attention-tracking"></a>注意力追蹤   
使用者所查看之位置或位置的資訊，是一種功能強大的工具。 它有助於評估設計的可用性，並識別工作流程中的問題，使其更有效率。
目視追蹤視覺效果和分析是各種應用程式區域中常見的作法。 有了 HoloLens 2，我們會提供新的維度來瞭解這一點，因為3D 全息圖可放置在真實世界的內容中，並據以進行評估。 [Mixed Reality 工具](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Main.html)組提供記錄和載入眼睛追蹤資料的基本範例，以及如何將其視覺化。
Microsoft 致力於促進創新，同時確保使用者對其眼睛追蹤資訊的使用方式有明智且透明的體驗。  我們將與我們的開發人員和 UX 小組合作，為協力廠商提供指導方針，以確保體驗是以使用者為中心。  


同屬此領域的其他應用程式包括： 
-   **遠端眼睛視覺效果：** 遠端眼睛視覺效果：視覺化遠端共同作業者所關注的內容，以提供立即的意見反應，並協助更精確的資訊處理。
-   **使用者研究研究：** 注意追蹤可協助研究人員深入瞭解使用者如何觀察並與自然環境互動，而不會干擾如何設計更 instinctual 的人類電腦互動。 目視追蹤可以提供在研究中的參與者未直接表達的資訊，但研究員可能很容易錯過。 
-   **訓練和效能監視：** 藉由在執行流程中更有效地找出瓶頸，來練習並將工作的執行優化。 目視追蹤可提供自然、即時和目標的資訊，以協助改善工作場所的訓練、生產力和安全性。 
-   **設計評估、行銷和取用者研究：** 目視追蹤可讓商業公司在真實世界的環境中執行行銷和取用者研究，或分析哪些東西會讓使用者注意，以改善產品或空間的設計。 

### <a name="additional-use-cases"></a>其他使用案例
- **遊戲：** 希望有超能力嗎？ 機會來了！ 您可以透過開始來 levitate 全像投影。 從您的眼睛放大鐳射字形狀-在 RoboRaid 中試用以 [進行 HoloLens 2](https://www.microsoft.com/p/roboraid/9nblggh5fv3j)。
將敵人變成石頭或凍結它們。 您可以用 X 光視線掃描建築物。 您想得到的都行！
要注意的是，不讓使用者覺得更多，請查看我們的 [眼睛型輸入設計指導方針](eye-gaze-interaction.md)。

- **表達虛擬人偶：** 眼睛追蹤可協助更具表達性的3D 虛擬人偶，方法是使用即時眼睛追蹤資料，以動畫顯示使用者所查看的內容。 

- **文字輸入：** 您可以使用眼睛追蹤作為低工作量文字輸入的替代方案，特別是當語音或手手不方便使用時。 

<br>

## <a name="using-eye-gaze-for-interaction"></a>使用眼睛進行互動
建立利用快速移動眼睛目標的互動可能是一項挑戰。
一方面，眼睛的移動速度很快，您需要特別注意如何使用眼睛的輸入，因為使用者可能會發現經驗太過或混亂。 另一方面，您也可以建立真正的神奇體驗，將激發您的使用者！ 若要協助您，請查看我們的主要優點、挑戰和設計建議，以進行 [互動](eye-gaze-interaction.md)。 
 
## <a name="fallback-solutions-when-eye-tracking-is-not-available"></a>當眼睛追蹤無法使用時的回溯解決方案

在罕見的情況下，可能無法使用眼睛追蹤資料。
這可能是因為以下是最常見的不同原因所致：
* 系統無法 [校正使用者](../calibration.md)。
* 使用者略過 [校正](../calibration.md)。    
* 已校正使用者，但決定不授與應用程式使用其眼睛追蹤資料的許可權。    
* 使用者有唯一的眼鏡或某些系統尚未支援的眼睛狀況。    
* 外部因素抑制可靠的眼睛追蹤，例如，因為眼睛前方的線，而非 HoloLens 面板或眼鏡、密集的直接陽光和遮蔽。   

因此，開發人員應該確保這些使用者有適當的回溯支援。 在 [ [DirectX 中的眼睛追蹤](../develop/native/gaze-in-directx.md#fallback-when-eye-tracking-isnt-available) ] 頁面上，我們會說明偵測是否有眼睛追蹤資料的必要 api。 

雖然某些使用者可能會基本思考模式決定要撤銷其眼睛追蹤資料的存取權，但對於不提供其眼追蹤資料存取權的隱私權而言，使用者體驗的取捨很有問題，但在某些情況下，這可能是不小心的。  
因此，如果您的應用程式使用眼睛追蹤，而且這是此體驗的重要部分，我們建議您明確地將此資訊傳達給使用者。     
請通知使用者，為什麼眼睛追蹤對您的應用程式而言是很重要的 (甚至可以列出一些增強的功能) ，以充分利用您的應用程式，協助使用者更瞭解他們所放棄的功能。   
協助使用者根據上述的檢查) ，找出可能無法 (眼睛追蹤的原因，並提供一些建議來快速排解可能的問題。     
比方說，如果您可以偵測到系統支援眼睛追蹤，則使用者會經過校正並獲得其許可權，但不會收到任何眼睛追蹤資料，而這可能會指向一些其他問題，例如汙跡或眼睛 pixels occluded。    
請注意，在罕見的情況下，眼睛追蹤可能無法正常運作的使用者。   
因此，請尊重，允許關閉或甚至停用在應用程式中啟用眼睛追蹤的提醒。

### <a name="fallback-for-apps-using-eye-gaze-as-a-primary-input-pointer"></a>使用眼睛作為主要輸入指標的應用程式的退回
如果您的應用程式使用眼睛來做為指標輸入，以快速地選取整個場景的全像投影，但無法使用眼睛追蹤資料，我們建議您回到頁首，然後開始顯示頭部眼的游標。 我們建議使用 timeout (例如 500-1500 ms) 來判斷是否要切換。 此動作可防止每次系統由於快速眼睛動作或動畫快遞和閃爍而短暫遺失追蹤時，就會顯示資料指標。 如果您是 Unity 開發人員，則已在混合現實工具組中處理自動回復至前端。 如果您是 DirectX 開發人員，您必須自行處理此參數。

### <a name="fallback-for-other-eye-tracking-specific-applications"></a>適用于其他眼睛追蹤專屬應用程式的回退
您的應用程式可能會以專為眼睛量身打造的獨特方式來使用眼睛。 例如，以動畫顯示圖片的眼睛，或是基於眼睛的注意，熱度圖依賴視覺效果的精確資訊。 在此情況下，不會有明確的回復。 如果無法使用眼睛追蹤，則可能只需要停用這些功能。
同樣地，我們建議您清楚地與可能不知道功能無法運作的使用者溝通。

<br>

此頁面希望您有大致的瞭解，讓您開始瞭解 HoloLens 2 的眼睛追蹤和眼睛輸入的角色。 若要開始進行開發，請查看有關眼睛的資訊，以瞭解如何與全像 [影像互動](eye-gaze-interaction.md)、 [在 Unity 中的眼睛](https://aka.ms/mrtk-eyes) ，以及 [DirectX 中的眼睛](../develop/native/gaze-in-directx.md)。


## <a name="see-also"></a>另請參閱
* [校正](../calibration.md)
* [舒適度](comfort.md)
* [眼部目光導向的互動](eye-gaze-interaction.md)
* [DirectX 中的眼睛](../develop/native/gaze-in-directx.md)
* [Unity 中的眼睛 (混合現實工具組) ](https://aka.ms/mrtk-eyes)
* [目光和行動](gaze-and-commit.md)
* [語音輸入](../out-of-scope/voice-design.md)


