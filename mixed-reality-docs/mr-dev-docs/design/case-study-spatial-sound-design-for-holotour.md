---
title: 案例研究 - HoloTour 的空間音效設計
description: 若要為 Microsoft HoloLens 建立真正的沉浸式3d 虛擬導覽，全景影片和全像攝影景象只是公式的一部分。
author: jsyltebo
ms.author: jsylte
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality、HoloLens、HoloTour、空間音效、個案研究、混合現實耳機、Windows Mixed Reality 耳機、虛擬實境耳機、HoloLens、MRTK、混合現實工具組、音訊
ms.openlocfilehash: b398ea7b3ddd85db85018da1852ed0c5ae410f625ff88bdda286e750a517d260
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2021
ms.locfileid: "115196441"
---
# <a name="case-study-spatial-sound-design-for-holotour"></a>案例研究： HoloTour 的空間音效設計

全景影片和全像全像景象是沉浸式 Microsoft HoloLens 導覽公式的一部分。 本文說明如何使用音效，讓您覺得實際上是在每個 HoloTour 的位置。

## <a name="the-tech"></a>技術

您在 HoloTour 中看到的美觀影像和全像攝影場景，只是可信混合現實體驗的一部分。 雖然全像是出現在使用者面前，HoloLens 可以從所有方向提供[空間音效](spatial-sound.md)，以提供更完整的感應式體驗。

空間音效提供提示，指出使用者應該輪流的方向，或讓使用者知道有更多的全像影像可在其空間內查看。 我們也可以直接將音效附加至全像影像，並持續更新來自使用者的全息圖方向和距離。 這項技術讓它看起來就像是直接來自該物件的音效。

針對 HoloTour，我們想要利用 HoloLens 的空間音效功能，因此我們建立了與影片同步處理的360度環境環境，以顯示特定位置的 sonic 重點。

## <a name="behind-the-scenes"></a>在幕後

我們建立了兩個不同位置的 HoloTour 體驗：羅馬和 Machu Picchu。 為了讓這些導覽感覺美觀且吸引人，我們想要從我們 filmed 的位置（而不是使用一般音效）捕獲音訊。

### <a name="capturing-the-audio"></a>捕獲音訊

在我們的案例研究中，我們將介紹 [HoloTour 的視覺內容](../out-of-scope/case-study-capturing-and-creating-content-for-holotour.md)，並討論相機設備的設計。 它是由3D 列印的機架中的14個 GoPro 攝影機所組成，其設計目的是要配合各架。 為了捕獲音訊，我們在攝影機下新增了一個十字麥克風陣列。 音效會送入基座基底的 compact 四聲道錄影單位。 我們選擇的麥克風夠好，但夠小，可以避免干擾攝影機。

![自訂製作的攝影機和麥克風 rig](images/camera-rig-microphones-300px.png)<br>
*自訂相機和麥克風 rig*

此安裝程式會以四個方向來捕捉音效。 我們已記錄足夠的資訊來重新建立空間音效的 3D aural 全景，我們稍後可以將其同步處理至360度的影片。

攝影機陣列音訊的挑戰之一，就是您正在 mercy 攝影機音效，例如 sirens、飛機或 high 接近尾聲。 為了確保我們所需的所有音效元素都有，我們使用了身歷聲和 mono 行動錄製程式，在每個位置的特定點上，捕捉到非同步環境音效。 這些錄製會提供音效設計工具的清楚內容，以新增感興趣的內容，並提升生產後的方向。

每個 capture day 都會產生許多檔案。 因此，請務必開發系統來追蹤哪些檔案對應至特定位置或攝影機。 我們的錄製單位已設定為依日期和「拍攝」號碼自動命名檔案。 在每天結束時，我們會將檔案備份至外部磁片磁碟機。 我們也發現 verbally 音訊錄製的開頭必須有很重要的。 這項預防措施可在發生檔案名稱問題時，輕鬆地識別內容。 由於影片和音訊是以個別媒體的形式錄製，而且必須在進入生產階段後進行同步處理，因此也很重要。

### <a name="editing-the-audio"></a>編輯音訊

在 capture 旅程之後回到 studio，組合方向和沉浸式 aural 體驗的第一個步驟，就是檢查某個位置的所有已捕獲音訊。 我們挑選最佳的採用，並找出可在整合期間套用的重點。 然後會編輯和清除音訊。 例如，以汽車為例，會持續一次或重複幾次，因此可能會從相同的捕獲會話以較安靜的環境音效取代。

設定位置的影片編輯之後，音效設計工具就可以同步處理對應的音訊。 此時，我們會評估攝影機和行動音效的捕獲，以決定哪些元素會建立最棒的沉浸式音訊場景。 我們發現將所有音效元素放入音訊編輯器中，並建立快速的線性模擬，以體驗不同的混合式想法，是很有用的。 此步驟為我們提供了更好的概念，讓我們知道何時可以建立實際的 HoloTour 場景。

### <a name="assembling-the-scene"></a>組合場景

建立3D 環境場景的第一個步驟，是建立一般背景環境迴圈音效的床，以支援場景中的其他功能和互動式音效元素。 我們採用以任何特定場景之設計準則所決定的全面方法。 有些場景可能會使用同步處理的相機捕捉來編制索引。 更多的「cinematic」時間可能需要策劃的方法，依賴分開放置音效、互動式元素和音樂。

當我們在攝影機-捕獲音訊上編制索引時，我們會將已啟用空間音效的環境音訊發射器，對應至相機的方向方向。 「中的攝影機」視圖會播放來自北麥克風的音訊，也同樣適用于其他的基線方向。 這些發射器都有全球鎖定，這表示當使用者切換其標頭時，音效會變更。 這項技術可有效地為位於該位置的音效建模。 聆聽 Piazza Navona 或 Pantheon，以取得使用良好的相機拍攝音訊組合的場景範例。

在不同的方法中，我們有時會使用放置於場景周圍的空間音效發射器來播放迴圈身歷聲環境。 這些發射器會播放隨機音量、音調和觸發頻率的一次性音效。 這項技術會建立具有更強方向的環境。 例如，在 Aguas Alienates 中，您可以聽到全景的每個象限如何具有特定的發射器，以反白顯示地理位置的特定區域，但共同合作來建立整體的沉浸式環境。

## <a name="tips-and-tricks"></a>秘訣與技巧

還有其他方式可以反白顯示方向性並改善深度，以充分利用 HoloLens 的空間音效功能。 我們在此提供了一份清單。 下一次嘗試 HoloTour 時，請聆聽這些效果。
* **尋找目標：** 當您查看全像攝影框架的特定物件或區域時，就會觸發這些音效。 例如，看看羅馬的 Piazza Navona 中的街道咖啡，以稍微觸發忙碌餐廳的聲音。
* **區域視覺：** HoloTour 的旅程包含特定的「勝過」，而您的導覽指南（以全像是輔助）可以深入探索主題。 比方說，在 Pantheon 的外觀上，會顯示從 Pantheon 內放置為3D 發射器的 oculus reverberating 音訊，鼓勵使用者探索內部。
* **增強的方向：** 在許多場景中，我們會以各種不同的方式來放置音效，以新增到方向。 例如，在 Pantheon 場景中，fountain 的音效是以個別的發射器來放置，足以讓使用者在接近播放空間時，能夠瞭解「sonic 視差」。 在秘魯的 Salinas de Maras 場景中，每個小型串流的音效都放在不同的發射器上，以建立更好的環境環境，以該位置的真實音效來圍繞使用者。
* **曲線發射器：** 這些發射器會根據其所連線物件的視覺化位置，移至3D 空間中。 其中一個範例是 Machu Picchu 中的訓練，我們使用曲線發射器來提供不同的方向和移動意義。
* **音樂和 SFX：** HoloTour 中表示更具樣式或 cinematic 方法的某些層面，會使用音樂和音效效果來提高情緒影響。 例如，在羅馬導覽結束時，gladiator 工作會使用 whooshes 和 stingers 等特殊效果，來強化幕後出現之標籤的效果。

## <a name="see-also"></a>另請參閱

* [空間音效](spatial-sound.md)
* [空間音效設計](spatial-sound-design.md)
* [Unity 中的空間音效](../develop/unity/spatial-sound-in-unity.md)
* [影片： Microsoft HoloLens： HoloTour](https://www.youtube.com/watch?v=pLd9WPlaMpY)
