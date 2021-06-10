---
title: 手部直接操作
description: 深入了解直接操作，這是一種讓使用者直接用手觸摸全像投影的輸入模型。
author: caseymeekhof
ms.author: cmeekhof
ms.date: 04/02/2019
ms.topic: article
ms.localizationpriority: high
keywords: 混合實境, 注視, 注視定向, 互動, 設計, 手部接近, HoloLens, 混合實境頭戴式裝置, windows 混合實境頭戴式裝置, 虛擬實境頭戴式裝置, MRTK, 混合實境工具組, 按鈕, 碰撞器, 週框方塊, 2D, 本能手勢
ms.openlocfilehash: 7a689f887bfd358b0d6e0826d41ef409bf887042
ms.sourcegitcommit: 9ae76b339968f035c703d9c1fe57ddecb33198e3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2021
ms.locfileid: "110600467"
---
# <a name="direct-manipulation-with-hands"></a>手部直接操作

![按鈕](images/UX_Hero_Manipulation.jpg)

直接操作是直接以雙手觸控全像投影的輸入模型。 這個概念背後的構想是要讓物件如同在真實環境中作動。 按鈕只要按下即可啟用、物件可藉由抓取來選取，2D 內容的行為則類似於虛擬觸控螢幕。 直接操作以能供性為基礎，這表示它很容易使用。 使用者不需學習任何象徵性的手勢。 所有互動都是以您可觸摸或抓取的視覺化元素為基礎。 我們將直接操作視為「近距離」輸入模型，因為它最適合用於伸手可及範圍內的內容互動。

## <a name="device-support"></a>裝置支援

<table>
<colgroup>
    <col width="33%" />
    <col width="22%" />
    <col width="22%" />
    <col width="22%" />
</colgroup>
<tr>
     <td><strong>輸入模型</strong></td>
     <td><a href="/hololens/hololens1-hardware"><strong>HoloLens (第 1 代)</strong></a></td>
     <td><a href="/hololens/hololens2-hardware"><strong>HoloLens 2</strong></a></td>
     <td><a href="/windows/mixed-reality/immersive-headset-hardware-details"><strong>沉浸式頭戴裝置</strong></a></td>
</tr>
<tr>
     <td>手部直接操作</td>
     <td>❌ 未支援</td>
     <td>✔️ 建議使用</td>
     <td>➕ 支援。  針對 UI，建議您改為使用<a href="point-and-commit.md">手部指向和行動</a>。</td>
    
</tr>
</table>


直接操作是 HoloLens 2 的主要輸入模型，HoloLens 2 使用新式連貫手部追蹤系統。 您也可使用運動控制器，搭配沉浸式頭戴裝置來操作輸入模型，但對於物件操作以外的互動，不建議以此作為主要機制。 在 HoloLens (第 1 代) 上無法進行直接操作。

<br>

---

## <a name="basic-hand-tracking-and-instinctual-interactions-demo"></a>基本的手追蹤和 instinctual 互動示範

如果您想要查看前端和眼睛追蹤設計的概念，請參閱下面 **的設計全息圖-標頭追蹤和眼睛追蹤** 影片示範。 當您完成時，請繼續進行，以深入瞭解特定主題。

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Microsofts-Designing-Holograms-Hand-Tracking-Chapter/player]

*這段影片取自「設計全像」應用程式 HoloLens 2 應用程式。下載並享有完整 [的體驗。](https://aka.ms/dhapp)*

## <a name="collidable-fingertip"></a>可碰撞的指尖

在 HoloLens 2 上，使用者的雙手會被辨識和解譯為左右兩手的架構模型。 若要實作直接以雙手觸控全像投影的概念，在理想情況下，五個 collider 可以連結至左右兩手架構模型的五個指尖。 但由於缺少觸覺反饋能力，10 個可碰撞的指尖可能對全像投影造成非預期且無法預測的衝突。 

我們建議僅將 collider 放在兩手的食指上。 可碰撞的食指指尖仍可作為使用中的觸控點，用於涉及其他手指的各種觸控手勢。 觸控手勢包括一指點按、一指點選、兩指點按和五指點按，如下所示：

:::row:::
    :::column:::
       ![可碰撞的指尖](images/Collidable-Fingertip.jpg)<br>
       **可碰撞的指尖**<br>
    :::column-end:::
    :::column:::
       ![一指點按](images/Collidable-Fingertip-1-finger-press.jpg)<br>
        **一指點按**<br>
    :::column-end:::
    :::column:::
       ![一指點選](images/Collidable-Fingertip-1-finger-tap.jpg)<br>
       **一指點選**<br>
    :::column-end:::
    :::column:::
       ![五指點按](images/Collidable-Fingertip-5-finger-press.jpg)<br>
       **五指點按**<br>
    :::column-end:::
:::row-end:::

<br>

---

### <a name="sphere-collider"></a>球體 collider

建議您不要使用隨機的一般形狀，而應使用球體 collider。 然後，您可以用視覺化的方式加以呈現，為近距離目標鎖定提供明確的提示。 球體的直徑應符合食指的粗細，以提高觸控的正確性。 呼叫手部 API，更容易擷取手指粗細的變數。

### <a name="fingertip-cursor"></a>指尖游標

除了在食指指尖上顯示可碰撞的球體以外，我們也建立了進階的指尖游標，以提供更好的近距離目標鎖定體驗。 這是連結至食指指尖的一個環狀游標。 此游標會根據鄰近性，在方向和大小方面動態回應目標，詳述如下：

* 當食指移向全像投影時，游標一律會與全像投影的表面平行，且其大小會逐漸縮減。
* 當手指接觸到表面時，游標會縮減為一個點，並發出觸控事件。

透過互動式反饋，使用者可執行高精確度的近距離目標鎖定工作，例如觸發超連結或按下按鈕，如下所示。 

:::row:::
    :::column:::
       ![指尖游標遠距](images/Fingertip-cursor-far.jpg)<br>
       **指尖游標遠距**<br>
    :::column-end:::
    :::column:::
       ![指尖游標近距](images/Fingertip-cursor-near.jpg)<br>
        **指尖游標近距**<br>
    :::column-end:::
    :::column:::
       ![指尖游標接觸](images/Fingertip-cursor-contact.jpg)<br>
       **指尖游標接觸**<br>
    :::column-end:::
:::row-end:::

<br>



## <a name="bounding-box-with-proximity-shader"></a>週框方塊與近接著色器

全像投影本身也須具備提供視覺和聽覺反饋的能力，以彌補觸覺反饋能力的不足。 為此，我們設計了週框方塊與近接著色器的概念。 週框方塊是足以包覆一個 3D 物件的最小體積區域。 週框方塊具有互動式呈現機制，名為近接著色器。 近接著色器的行為如下：

:::row:::
    :::column:::
       ![暫留 (遠距) 視覺化回饋](images/bounding-box-with-proximity-shader-hover-far.jpg)<br>
       **暫留 (遠距)**<br>
       當食指進入範圍內時，手指焦點即會投射在週框方塊的表面。
    :::column-end:::
    :::column:::
       ![暫留 (近距) 視覺化回饋](images/bounding-box-with-proximity-shader-hover-near.jpg)<br>
        **暫留 (近距)**<br>
        當指尖越來越接近表面時，焦點會縮小。
    :::column-end:::
    :::column:::
       ![接觸開始](images/bounding-box-with-proximity-shader-begin-contact.jpg)<br>
       **接觸開始**<br>
       手指一碰到表面時，整個週框方塊就會變色，或產生視覺效果以反映觸碰狀態。
    :::column-end:::
    :::column:::
       ![接觸結束](images/bounding-box-with-proximity-shader-end-contact.jpg)<br>
       **接觸結束**<br>
       此外也可以啟用音效來補強視覺的觸碰反饋。
    :::column-end:::
:::row-end:::

<br>

---

## <a name="pressable-button"></a>可點按的按鈕

有了可碰撞的指尖，使用者即可與基本的全像攝影 UI 元件互動，例如可點按的按鈕。 可點按的按鈕是專為直接手指點按設計的全像攝影按鈕。 同樣地，由於缺少觸覺反饋能力，可點按的按鈕也設有若干機制，來處理觸覺反饋能力的相關問題。

* 第一項機制是具有近接著色器的週框方塊，其詳細說明請見上一節。 它可讓使用者在接近及觸碰按鈕時更能清楚感知鄰近性。
* 第二項機制是下壓。 下壓會在指尖接觸到按鈕後，產生按下的感覺。 此機制能確保按鈕會緊隨著指尖沿深度軸移動。 在按鈕達到所選的深度 (按下) 或離開該深度 (放開) 之後，就會觸發按鈕。
* 在觸發按鈕時應加上音效以增強反饋。

:::row:::
    :::column:::
       ![可點按的按鈕遠距](images/pressable-button-far.jpg)<br>
       **手指遠離**<br>
    :::column-end:::
    :::column:::
       ![可點按的按鈕近距](images/pressable-button-approach.jpg)<br>
        **手指靠近**<br>
    :::column-end:::
    :::column:::
       ![可點按的按鈕接觸開始](images/pressable-button-contact.jpg)<br>
       **接觸開始**<br>
    :::column-end:::
    :::column:::
       ![可點按的按鈕點按](images/pressable-button-press.jpg)<br>
       **按下**<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="2d-slate-interaction"></a>2D 平板互動

2D [平板](slate.md)是用來裝載 2D 應用程式內容 (例如網頁瀏覽器) 的全像攝影容器。 透過直接操作與 2D 平板互動的設計概念，和與實體觸控螢幕互動的設計概念相同。

### <a name="to-interact-with-the-slate-contact"></a>與觸控平板互動

:::row:::
    :::column:::
       ![觸控](images/2d-slate-interaction-touch.jpg)<br>
       **觸控**<br>
       以食指按下超連結或按鈕。
    :::column-end:::
    :::column:::
       ![捲動](images/2d-slate-interaction-scroll2.jpg)<br>
        **捲動**<br>
        以食指向上和向下捲動平板內容。
    :::column-end:::
    :::column:::
       ![縮放](images/2d-slate-interaction-zoom2.jpg)<br>
       **縮放**<br>
       使用者可用兩根食指，根據手指的相對移動來放大和縮小平板內容。
    :::column-end:::
:::row-end:::


### <a name="for-manipulating-the-2d-slate-itself"></a>操作 2D 平板本身

:::row:::
    :::column:::
       ![顯示抓取和拖曳功能的圖形](images/manipulate-2d-slate-move.jpg)<br>
       **移動**<br>
       將手靠近角落或邊緣時，可顯示最接近的操作能供性。 抓取 2D 平板上方的 holobar，可以移動整個平板。
    :::column-end:::
    :::column:::
       ![顯示縮放功能的圖形](images/manipulate-2d-slate-scale.jpg)<br>
        **縮放比例**<br>
        抓取操作能供性，並透過角落能供性進行統一縮放。
    :::column-end:::
    :::column:::
       ![自動重排](images/manipulate-2d-slate-reflow.jpg)<br>
       **自動重排**<br>
       抓取操作能供性，透過邊緣能供性進行自動重排。
    :::column-end:::
:::row-end:::

<br>

---


## <a name="3d-object-manipulation"></a>3D 物件操作

HoloLens 2 可讓使用者將週框方塊套用至每個 3D 物件，以便用手指引及操作 3D 全像攝影物件。 週框方塊可透過其近接著色器提供更確切的深度認知。 週框方塊衍生出兩種 3D 物件操作方法。

### <a name="affordance-based-manipulation"></a>能供性操作

能供性操作可讓您透過週框方塊及其周圍的操作能供性來操作 3D 物件。 

:::row:::
    :::column:::
       ![顯示物件週框方塊和移動功能的圖形](images/3d-object-manipulation-move.jpg)<br>
       **移動**<br>
       當使用者的手接近 3D 物件時，就會顯示週框方塊和最接近的能供性。 使用者可以抓取週框方塊來移動整個物件。
    :::column-end:::
    :::column:::
       ![顯示抓取物件邊緣以旋轉的使用者圖形](images/3d-object-manipulation-rotate.jpg)<br>
        **旋轉**<br>
        使用者可以抓取邊緣能供性來進行旋轉。
    :::column-end:::
    :::column:::
       ![顯示抓取物件角落以縮放的使用者圖形](images/3d-object-manipulation-scale.jpg)<br>
       **縮放比例**<br>
       使用者可以抓取角落能供性來執行統一尺寸調整。
    :::column-end:::
:::row-end:::

<br>


### <a name="non-affordance-based-manipulation"></a>非能供性操作

非能供性操作不會將能供性連結至週框方塊。 使用者只能顯示週框方塊，然後直接與它互動。 若以一隻手抓住週框方塊，物件的轉譯和旋轉會與那隻手的動作和方向相關聯。 以雙手抓住物件時，使用者可以根據兩隻手的相對動作來轉譯、縮放及旋轉物件。

特定操作需要精確度。 建議您使用 **能供性操作**，因為它可提供高層級的細微性。 針對彈性操作，建議您使用 **非能供性操作**，因為它可帶來即時而有趣的體驗。

<br>

---


## <a name="instinctual-gestures"></a>本能手勢

在 HoloLens (第 1 代) 推出時，我們曾教過使用者幾個預先定義的手勢，例如綻開和空中點選。 而在使用 HoloLens 2 時，使用者並不需要記住任何象徵性的手勢。 使用者與全像投影和內容互動時所需使用的所有必要手勢，都是符合本能的。 協助使用者透過 UI 能供性的設計執行手勢，他們就能學會本能手勢。

例如，如果我們引導使用者以兩指捏合抓取某個物件或控制點，表示該物件或控制點應該很小。 如果我們要使用者進行五指抓取，表示該物件或控制點應相對較大。 與按鈕類似，微小的按鈕會使得使用者只能用單一手指進行按壓。 較大的按鈕會促使使用者使用手掌進行按壓。


:::row:::
    :::column:::
       ![顯示抓取小型物件以移動的使用者圖形](images/instinctual-gestures-smallobject.jpg)<br>
       **小型物件**<br>
    :::column-end:::
    :::column:::
       ![顯示抓取中型物件以移動的使用者圖形](images/instinctual-gestures-mediumobject.jpg)<br>
        **中型物件**<br>
    :::column-end:::
    :::column:::
       ![顯示抓取大型物件以移動的使用者圖形](images/instinctual-gestures-largeobject.jpg)<br>
       **大型物件**<br>
    :::column-end:::
:::row-end:::


<br>

---

<br>

## <a name="symmetric-design-between-hands-and-6-dof-controllers"></a>手部與 6 DoF 控制器之間的對稱設計

您可能已經注意到，AR 中的手勢與 VR 中的運動控制器在互動方式上有其相似之處。 這兩種輸入在其各自的環境中都可用來觸發直接操作。 在 HoloLens 2 中，近距離以手抓取並拖曳的效用，非常類似於 WMR 運動控制器上的抓取按鈕所能做到的。 這種相似性可讓使用者在兩種平台上都能採用熟悉的互動方式，且若您決定在這兩個平台之間移轉應用程式，這一點可能也有幫助。

<br>

---

## <a name="optimize-with-eye-tracking"></a>透過眼球追蹤達到最佳效果

直接操作若能如預期運作，將可達到奇妙的效果。 但若無法順利將手移到想要的位置，而老是無意中觸發全像投影，就會出現挫敗感。 眼球追蹤或許有助於判斷使用者真正的意圖。

* **時機**：避免無意中觸發操作回應。 眼球追蹤有助於了解使用者目前從事的活動。
例如，想像您在閱讀全像攝影 (指示) 文字時，您伸手要去拿實際環境中的工具。

此時，您的手不小心劃過某個您根本沒留意過的互動式全像攝影按鈕。 例如，該按鈕可能不在使用者的視野 (FoV) 內。

如果使用者已有一段時間未注視某個全像投影，但仍偵測到觸碰或抓取事件，表示此互動很可能是無意的。

* **標的**：除了處理誤判的啟用以外，它還有助於判斷所應抓取或觸碰的全像投影，因為從您的視角可能無法看出精準的交叉點，尤其是有數個全像投影的位置彼此十分靠近時。

  雖然 HoloLens 2 的眼球追蹤在判斷眼部注視時會因其精準度而有所限制，但對近距離互動而言仍不失為有利的工具，因為透過手部輸入互動時，會有深度的差異。 舉例而言，要判斷您的手是在全像投影的後面還是前面，以精確地抓取操作工具，有時是很困難的。

* **目的地**：運用使用者在執行快速拋投手勢時看往何處的相關資訊。 抓取全像投影並約略拋向您要的目的地。  

    雖然這有時行得通，但快速執行手勢可能會導致目的地嚴重失準。 不過，同時運用眼球追蹤或可改善手勢的準確度。

<br>

---

## <a name="manipulation-in-mrtk-mixed-reality-toolkit-for-unity"></a>MRTK (混合實境工具組) 中適用於 Unity 的操作
透過 **[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** ，您可以使用指令碼 **ObjectManipulator** 輕鬆執行常見的操作行為。 使用 ObjectManipulator，您可以直接用手或透過手部射線來抓取和移動物件。 它也支援雙手操作來縮放和旋轉物件。

* [MRTK - 操作](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/object-manipulator)

---

## <a name="see-also"></a>另請參閱

* [頭部目光和行動](gaze-and-commit.md)
* [手部指向和行動](point-and-commit.md)
* [本能互動](interaction-fundamentals.md)