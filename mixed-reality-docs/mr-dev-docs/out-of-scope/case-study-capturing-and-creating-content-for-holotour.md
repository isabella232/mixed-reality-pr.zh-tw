---
title: 案例研究-HoloTour
description: HoloTour for Microsoft HoloLens 提供全球 iconic 地點的沉浸式3D 個人導覽。 本案例研究將逐步解說如何捕獲和建立用於 HoloTour 的內容。
author: dannyaskew
ms.author: daaske
ms.date: 03/21/2018
ms.topic: article
keywords: HoloTour、HoloLens、Windows Mixed Reality
ms.openlocfilehash: 9908327a1b8e70eef73d3f98adb7c75615e8e098
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/03/2020
ms.locfileid: "91679797"
---
# <a name="case-study---holotour"></a>案例研究-HoloTour

HoloTour for Microsoft HoloLens 提供全球 iconic 地點的沉浸式3D 個人導覽。 當設計人員、演出者、生產者、音訊設計工具和開發人員參與此專案時，為已知位置建立 convincingly 的實際3D 轉譯，會採用獨特的創意與技術 wizardry 融合。 本案例研究將逐步解說如何捕獲和建立用於 HoloTour 的內容。

## <a name="the-tech"></a>技術

有了 HoloTour，我們想要讓人們能夠造訪一些全球最棒的目的地，像是在秘魯的 [Machu Picchu 毀損](https://en.wikipedia.org/wiki/Machu_Picchu) 或義大利日 [Piazza Navona](https://en.wikipedia.org/wiki/Piazza_Navona) ，直接從他們自己的聊天室。 我們的團隊將其目標 HoloTour 為「讓您覺得您真的在那裡」。 不只是圖片或影片所需的體驗。 利用 HoloLens 的獨特顯示器、追蹤和音訊技術，我們相信我們可以將您傳輸到另一個位置。 我們需要為每個流覽的位置，抓住堪薩斯州、音效和三維幾何，然後在我們的應用程式內重新建立。

為了達到此目的，我們需要一個具有方向性音訊捕捉的360°攝影機設備。 它需要以極高的解析度來捕捉，讓素材在 HoloLens 上播放時看起來很簡潔，而且攝影機必須放置在一起，才能將裝訂成品降至最低。 我們想要完全有球形的範圍，而不是在範圍內，但在您的上方和下方。 Rig 也必須是可移植的，才能讓我們在世界各地。 我們評估了現成可用的選項，併發現它們沒有足夠的能力來實現我們的願景，可能是因為解析度、成本或大小。 如果找不到符合需求的攝影機 rig，則必須自行建立。

### <a name="building-the-rig"></a>建立 rig

第一個版本（從紙箱、Velcro、管道磁帶和14個 GoPro 攝影機）是 MacGyver 很榮幸的東西。 從低端解決方案到自訂製造的 rig 進行審核之後，GoPro 攝影機最終是最適合我們的選擇，因為它們很小、價格實惠，而且具有容易使用的記憶體儲存體。 小型外型規格特別重要，因為它可讓我們將相機保持在一起，而相機之間的距離越小，則裝訂成品就越小。 我們獨特的攝影機相片順序可讓我們取得完整的球體涵蓋範圍， *再加上* 足夠的重迭，以智慧地對齊攝影機，並在進行拼接程式時使某些成品順暢

利用 HoloLens 的 [空間音效](../design/spatial-sound.md) 功能，對於創造 convincingly 的真正沉浸式體驗非常重要。 我們使用了四個麥克風的陣列，其位於您的攝影機下，這會以四個方向從相機的位置捕捉音效，提供足夠的資訊讓我們在幕後建立空間音效。

![我們的360°攝影機設備是針對 Pantheon 以外的 filming 進行設定。](images/camera-pantheon-200px.png)

我們的360°攝影機設備是針對 Pantheon 以外的 filming 進行設定。 


我們已將自製的測試人員帶到 Rattlesnake 附近的凸緣來進行測試，並在走去加加頂端取得景象。 結果雖然比您今天在 HoloTour 中所看到的位置明顯較不完善，但讓我們相信您的 rig 設計很有説明，讓您覺得您真的很滿意。

我們已將 Velcro 和紙箱的 rig 升級為3D 列印的攝影機，並購買 GoPro 攝影機的外部電池套件，以簡化電池管理。 接著，我們進行了更廣泛的測試，向下移動至三藩市，以建立城市的 coast 和 iconic 黃金閘道的縮圖。 這是我們在 HoloTour 中流覽的大部分位置所使用的相機 rig。

![Machu Picchu 中的360°攝影機 rig filming。](images/camera-machu-pichu-500px.png)

Machu Picchu 中的360°攝影機 rig filming。 

## <a name="behind-the-scenes"></a>在幕後

在 filming 之前，我們需要找出我們想要包含在虛擬導覽上的位置。 羅馬是我們打算寄出的第一個位置，我們想要讓它正確，因此我們決定事先進行 scouting 行程。 我們傳送了六名人員（包括演出者、設計師和生產者）的團隊，讓他們親自造訪我們所考慮的網站。 旅程大約需要9天–2.5 用於旅遊，filming 的其餘部分。  (針對 Machu Picchu，我們選擇不要進行 scout 行程，事先研究並預約幾天的緩衝區以進行 filming。 ) 

在羅馬期間，小組會取得每個區域的相片，並記下有趣的事實，以及實際的考慮，例如，移動到每個位置的困難度，以及因 crowds 或限制而造成的電影。 這聽起來可能像度假，但其實有很多工作。 早上早上開始使用，並不會停止，直到夜晚。 每晚上傳一份素材，讓小組回到西雅圖進行評論。 

![我們的「我們的捕獲」是以羅馬。](images/holotour-filming-crew-rome-500px.jpg) 

我們的「我們的捕獲」是以羅馬。 


Scout 行程完成之後，就會針對實際 filming 進行最終的計畫。 這需要一個詳細的清單，說明我們要在哪一天、哪些時候，以及在什麼時候的電影。 每日海外都很昂貴，因此這些旅程需要很有效率。 我們在羅馬中預訂了輔助線和處理常式，可協助我們在每日從日出到終止之後，都能完全使用。 我們需要取得最佳的鏡頭，才能讓您覺得真正的樣子。

### <a name="capturing-the-video"></a>捕獲影片

在 capture 期間進行一些簡單的作業，可讓後續處理作業更容易。 例如，當您將多個相機的影像結合在一起時，您最後會得到視覺構件，因為每個相機的觀點都稍微不同。 較接近的物件是相機、視圖之間的差異越大，以及裝訂成品將會變大。 以下是將問題視覺化的簡單方式：將您的 thumb 放在臉部前方，並只查看一眼。 立即切換眼睛。 您會看到您的 thumb 顯示為相對於背景的移動。 如果您的臉部更遠離開您的臉部，並重複實驗，那麼您的 thumb 將會變得更少。 這種明顯的移動類似于我們所面臨的拼接問題：您的眼睛（像是攝影機）看不到完全相同的影像，因為它們是以短距離隔開。

因為在 filming 時可以更輕鬆地預防最糟的成品，而不是在後置處理中加以修正，因此我們會嘗試讓其他人和專案遠離相機，而不需要將特寫物件拼接在一起。 在我們的過程中維持大規模清除，是我們在進行診斷時最大的挑戰之一，而我們必須有創意才能讓它運作。 使用本機指南對於管理 crowds 有很大的説明，但我們也發現，使用正負號（有時是小型的圓錐或 bean 包）來標示 filming 空間相當有效，尤其是因為我們只需要在每個位置取得少量的素材。 取得良好的捕獲通常是在早上很早抵達的最佳方式，在大部分的人顯示之前都是如此。

還有一些其他有用的捕獲技巧，直接來自傳統的電影實務。 例如，我們在所有的相機上都使用了顏色更正卡，並在稍後取得材質和物件的參考相片。 

![顯示色彩校正卡的 Machu Picchu 粗略剪下。](images/rough-cut-machu-picchu-500px.png)

Pantheon 素材在進行裝訂之前的粗略剪下。

### <a name="processing-the-video"></a>處理影片

捕捉360的內容只是第一個步驟：需要進行大量處理，才能將我們所捕獲的原始攝影機素材轉換成您在 HoloTour 中看到的最終資產。 離開後，我們需要從14個不同的相機摘要中拍攝影片，並將其轉換成具有最少量構件的單一持續影片。 我們的藝術團隊使用許多工具來結合和波蘭文已捕捉的影片，而我們開發了管線，盡可能將處理優化。 您必須將這種素材拼接在一起、校正色彩，然後再加以組合，以移除雜亂的元素和成品，或是新增生命和運動的補充隨身，其目標是要加強實際效果。

![Pantheon 素材在進行裝訂之前的粗略剪下。](images/rough-cut-pantheon-500px.png)

Pantheon 素材在進行裝訂之前的粗略剪下。 


為了將影片結合在一起，我們使用了稱為 [PTGui](https://www.ptgui.com/) 的工具，並將它整合到我們的處理管線中。 在後置處理過程中，我們從影片中解壓縮的是畫面格，並找到針對其中一個畫面格看起來很不錯的拼接圖樣。 接著，我們會將該模式套用至我們所撰寫的自訂外掛程式，讓我們的視頻演出者可以在效果過之後，直接微調及調整拼接圖樣。 

![PTGui 的螢幕擷取畫面，其中顯示拼接 Pantheon 的素材。](images/stitching-tool-pantheon-500px.png)

PTGui 的螢幕擷取畫面，其中顯示拼接 Pantheon 的素材。 


### <a name="video-playback"></a>影片播放

在處理完素材之後，我們有一段流暢的影片，但其實很大，大約是8K 的解析度。 解碼影片的成本很高，而且有很少的電腦可以處理8K 的影片，因此下一項挑戰就是尋找在 HoloLens 上播放這部影片的途徑。 我們開發了一些策略來避免解碼的成本，但仍讓使用者感覺像是觀看整段影片。

最簡單的優化是避免解碼部分不會變得太大的影片。 我們撰寫了一個工具來識別每個場景中幾乎沒有任何動作的區域。 針對這些區域，我們會顯示靜態影像，而不是在每個框架中解碼影片。 為了達成這一點，我們將大量的影片分成更小的區塊。

我們也會確定我們解碼的每個圖元都是最有效率的使用方式。 我們實驗了壓縮技術來降低影片的大小;我們會根據所投射幾何的多邊形來分割影片區域;我們調整了 UVs，並根據包含的不同多邊形詳細資料來 repacked 影片。 這項工作的結果，是以單一8k 影片的形式啟動，而這段影片在正確地重新投射到場景之前，會一直看起來幾乎無法理解。 針對瞭解材質對應和 UV 封裝的遊戲開發人員，這可能看起來很熟悉。 

![優化之前的 Pantheon 完整觀點。](images/pantheon-before-optimization-500px.png) 

優化之前的 Pantheon 完整觀點。 


![Pantheon 的上半部，處理影片播放。](images/pantheon-process-video-playback-500px.png) 

Pantheon 的上半部，處理影片播放。 


![優化和封裝之後的單一影片區域範例。](images/single-video-region-after-optimization-500px.png) 

優化和封裝之後的單一影片區域範例。 


我們使用的另一種技巧是避免解碼您未主動觀賞的影片。 在 HoloTour 中，您在任何指定的時間都只能看到一部分的完整場景。 我們只會在您的視野 (FOV) 的內部或不久之外解碼影片。 當您旋轉頭部時，我們會開始播放影片中現在位於 FOV 中的區域，並停止播放不再存在的影片中。 大部分的人都不會注意到這種情況，但如果您很快就會看到影片，您會看到影片需要一秒鐘的時間才能開始，此時您會看到一個靜態影像，當它準備好後，就會淡回影片。

為了讓此策略運作，我們開發了大量的影片播放系統。 我們已優化低層級的播放程式碼，讓影片切換變得非常有效率。 此外，我們必須以特殊方式編碼我們的影片，讓您隨時都能快速切換到任何影片。 這種播放管線花費大量的開發時間，因此我們會分階段執行。 我們開始使用較簡單的系統，它的效率較低，但允許的設計人員和演出者可以使用此體驗，並讓我們以更健全的播放系統（可讓我們在最終品質列）提供更佳的改進。 此最終系統擁有在 Unity 中建立的自訂工具，可在場景內設定影片並監視播放引擎。

### <a name="recreating-near-space-objects-in-3d"></a>在3D 中重建近空間物件

影片會構成您在 HoloTour 中所看到的大部分內容，但是有一些與您相近的3D 物件，例如 Piazza Navona 中的繪圖、Pantheon 外的 fountain，或您針對排氣場景所參與的熱空氣球。 這些3D 物件很重要，因為人類深度感知非常好用，但不太理想。 我們可以在距離中找出影片，但為了讓使用者可以四處四處看看他們的空間，而鄰近的物件則需要深度。 這項技術與您可能會在自然歷程記錄博物館中看到的一樣，也就是在前景中有實體造景、工廠和動物 specimens 的 diorama，但 recedes 在背景中以巧妙地遮罩遮罩的方式繪製。

有些物件就是我們建立並新增至場景的3D 資產，以增強體驗。 繪製和熱的氣球會落在這個類別中，因為我們在 filmed 時並不存在。 與遊戲資產類似，它們是由小組的3D 演出者所建立，並有適當的紋理。 我們將這些放在幕後的地方，而遊戲引擎可以將它們轉譯成兩個 HoloLens 顯示器，讓它們顯示為3D 物件。

其他資產（例如 Pantheon 以外的 fountain）是存在於我們即將推出影片之位置中的真實物件，但若要將這些物件從影片中移出，並將這些物件放在影片中，我們必須執行一些動作。

首先，我們需要有關每個物件的其他資訊。 在 filming 的位置，我們的團隊會為這些物件捕捉許多參考圖，讓我們有足夠的詳細影像來精確地重新建立紋理。 小組也執行了 [攝影測量](https://en.wikipedia.org/wiki/Photogrammetry) 掃描，它會從數十個2d 影像中建立3d 模型，讓我們以完美的比例提供物件的粗略模型。

當我們處理我們的影片時，將會從影片中移除以3D 標記法之後將取代的物件。 3D 資產是以攝影測量模型為基礎，但我們的演出者會加以清除和簡化。 對於某些物件而言，我們可以使用影片的元件（例如 fountain 上的水材質），但大部分的 fountain 現在都是3D 物件，可讓使用者在體驗的有限空間中觀察深度並加以解說。 有接近空間的物件（例如這樣）會大幅增加其真實性的意義，並有助於將虛擬位置的使用者接地。 

![已移除 fountain 的 Pantheon 素材。 它會以3D 資產取代。](images/object-removal-pantheon-500px.png)

已移除 fountain 的 Pantheon 素材。 它會以3D 資產取代。


## <a name="final-thoughts"></a>最後的想法

很明顯地，建立此內容比我們在這裡所討論的還多。 有幾個場景，我們想要將它們稱為「不可能的觀點」，包括熱的氣球，以及 Colosseum 中的 gladiator 打擊，以採取更具創意的方式。 我們將在未來的案例研究中解決這些情況。

我們希望在生產期間共用的一些較大挑戰的解決方案，對其他開發人員很有説明，而且您也會想要使用其中一些技巧來為 HoloLens 建立您自己的沉浸式體驗。  (如果您這樣做，請務必在 [HoloLens 應用程式開發論壇](https://forums.hololens.com/)中與我們分享！ ) 

## <a name="about-the-authors"></a>關於作者

<table style="border:0">
<tr>
<td style="border:0" width="60px"> <img alt="David Haley" width="60" height="60" src="images/haley.png" /></td>
<td style="border:0" width="408"> <b>David Haley</b> 是一位資深開發人員，他們學到更多有關相機 rig 和影片播放的資訊，而不是他想像過 HoloTour。</td>
<td style="border:0" width="60px"> <img alt="Danny Askew" width="60" height="60" src="images/askew.png" /></td>
<td style="border:0" width="408"> <b>Danny Askew</b> 是一位影片演出者，可確保您的羅馬進度盡可能完美。</td>
</tr>
<tr>
<td style="border:0" width="60px"> <img alt="Jason Syltebo" width="60" height="60" src="images/syltebo.png" /></td>
<td style="border:0" width="408"> <b>Jason Syltebo</b> 是一種音訊設計工具，可確保您可以體驗您所造訪之每個目的地的 soundscape，即使您回頭回來也是如此。</td>
<td style="border:0" width="60px"> <img alt="Travis Steiner" width="60" height="60" src="images/steiner.png" /></td>
<td style="border:0" width="408"> <b>Travis Steiner</b> 是一位設計主管，負責研究和 scouted 地點、建立旅程計畫，以及在現場導向 filming。</td>
</tr>
</table>



## <a name="see-also"></a>另請參閱
* [影片： Microsoft HoloLens： HoloTour](https://www.youtube.com/watch?v=pLd9WPlaMpY)
